---
tags:
  - databaze
  - databaze_a_web
  - tomas
---
## 1. Normální forma (1NF)
**Podmínky:**
- Každá tabulka musí mít jednoznačný primární klíč.
- Všechny sloupce tabulky musí obsahovat pouze atomické (nedělitelné) hodnoty.

**Příklad porušení 1NF:**
- Tabulka „Employee“ obsahuje sloupec „Subordinate“, který obsahuje složený typ (seznam zaměstnanců), což porušuje 1NF:

| Id  | Name           | Subordinate             | Boss          |
|-----|----------------|-------------------------|---------------|
| 1   | John Goodman   | [Person1, Person2, ...] | Person5       |


**Oprava:**
- Rozdělit složené typy do samostatných tabulek:

**Tabulka: Employee:**

| Id  | Name           | Boss       |
|-----|----------------|------------|
| 1   | John Goodman   | Person5    |

**Tabulka: Subordinates:**

| EmployeeId | SubordinateId |
|------------|---------------|
| 1          | Person1       |
| 1          | Person2       |


## 2. Normální forma (2NF)
**Podmínky:**
- Splňuje požadavky 1NF.
- Všechny <mark style="background: #FFF3A3A6;">neklíčové atributy</mark> musí být plně závislé na <mark style="background: #FFF3A3A6;">celém primárním klíči</mark>, nikoli pouze na <mark style="background: #FFF3A3A6;">části</mark> primárního klíče.

**Příklad porušení 2NF:**
- Tabulka „Company“ obsahuje atribut „HQ“, který je závislý pouze na části složeného klíče „Company“, nikoliv na celém klíči „Company, DB server“:

| Company    | DB server | HQ       | Purchase date |
|------------|-----------|----------|---------------|
| John's firm| Oracle    | Paris    | 1995          |
| John's firm| MS SQL    | Paris    | 2001          |
| Paul's firm| IBM DB2   | London   | 2004          |

**Oprava:**
- Rozdělit tabulku do dvou, aby byl odstraněn částečný závislý atribut „HQ“:
Tabulka: CompanyDBServer

| Company    | DB server | Purchase date |
|------------|-----------|---------------|
| John's firm| Oracle    | 1995          |
| John's firm| MS SQL    | 2001          |

Tabulka: CompanyHQ

| Company    | HQ       |
|------------|----------|
| John's firm| Paris    |
| Paul's firm| London   |

## 3. Normální forma (3NF)
**Podmínky:**
- Splňuje požadavky 2NF.
- Žádný neklíčový atribut nesmí záviset na jiném neklíčovém atributu (transitivní závislost).

**Příklad porušení 3NF:**
- Tabulka „Company“ obsahuje atribut „HQ“, který je transitivně závislý na klíči „Company“ přes atribut „ZIPcode“:

| Company     | ZIPcode  | HQ      |
| ----------- | -------- | ------- |
| John's firm | CZ 11800 | Prague  |
| Paul's firm | CZ 70833 | Ostrava |

**Oprava:**
- Rozdělit tabulku tak, aby byly odstraněny transitivní závislosti:

Tabulka: CompanyZIP

| Company    | ZIPcode  |
|------------|----------|
| John's firm| CZ 11800 |
| Paul's firm| CZ 70833 |

Tabulka: ZIPcodeHQ

| ZIPcode   | HQ      |
|-----------|---------|
| CZ 11800  | Prague  |
| CZ 70833  | Ostrava |

## Boyce-Coddova normální forma (BCNF)
**Podmínky:**
- Splňuje požadavky 3NF.
- Každá determinantní závislost musí být kandidátní klíč.

**Příklad porušení BCNF:**
- Tabulka „Flights“ obsahuje závislost „Destination → Pilot“, kde „Destination“ není superklíčem:

| Destination | Pilot       | Plane  | Day    |
| ----------- | ----------- | ------ | ------ |
| Paris       | cpt. Oiseau | Boeing | Monday |
| Berlin      | cpt. Vogel  | Airbus | Monday |

**Oprava:**
- Rozdělit tabulku tak, aby byly odstraněny závislosti, kde determinant není superklíčem:

Tabulka: Destinations

| Destination | Pilot       |
|-------------|-------------|
| Paris       | cpt. Oiseau |
| Berlin      | cpt. Vogel  |

Tabulka: FlightDetails

| Destination | Plane  | Day     |
|-------------|--------|---------|
| Paris       | Boeing | Monday  |
| Berlin      | Airbus | Monday  |
