---
dg-publish: true
tags:
  - web
  - tomas
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT

### Jak položit dotaz v GraphQL

GraphQL je dotazovací jazyk pro API, který vám umožňuje přesně specifikovat, jaká data chcete získat. Zde je příklad základního dotazu v GraphQL:

```json
{
  user(id: "1") {
    id
    name
    email
    posts {
      id
      title
    }
  }
}
```

Tento dotaz žádá o uživatele s ID „1“ a získá jeho `id`, `name`, `email` a seznam `posts`, které obsahují `id` a `title` každého příspěvku.

#### Příklad: Dotaz v GraphQL s filtry, `AND`, `OR` a podobnými operátory

Pokud chceme filtrovat podle více atributů v GraphQL, můžeme v definici schématu přidat vstupní typy pro filtrování a podporu logických operátorů, jako jsou `AND` a `OR`. Níže je příklad, jak by to mohlo vypadat.

##### Příklad schématu s filtry

```json
type Query {
  users(filter: UserFilter): [User]
}

input UserFilter {
  name: String
  age: Int
  status: String
  AND: [UserFilter]
  OR: [UserFilter]
}
```

V tomto schématu:
- `UserFilter` je vstupní typ, který umožňuje filtrovat podle různých atributů (`name`, `age`, `status`) a obsahuje možnosti pro kombinaci filtrů pomocí `AND` a `OR`.

##### Příklad dotazu s filtry

```json
{
  users(filter: {
    OR: [
      { name: "Jan" },
      { AND: [{ age: 30 }, { status: "aktivní" }] }
    ]
  }) {
    id
    name
    age
    status
  }
}
```

V tomto příkladu:
- Dotazujeme uživatele (`users`) a aplikujeme filtry.
- `OR` v tomto případě zkontroluje, zda buď uživatelské `name` je "Jan", nebo zda jsou oba podmínky (`age` je 30 a `status` je "aktivní") splněny.

#### Group By v GraphQL

GraphQL nativně nepodporuje funkce jako `GROUP BY` známé z SQL. Avšak seskupování a agregace dat je možné implementovat prostřednictvím specifických resolverů na straně serveru nebo speciálních typů dotazů.

##### Příklad seskupení (Group By) na straně serveru

Místo tradičního `GROUP BY` můžeme v GraphQL definovat speciální dotaz, který vrátí data seskupená podle určitých atributů.

###### Příklad schématu

```json
type Query {
  usersGroupedByStatus: [UsersGroupedByStatus]
}

type UsersGroupedByStatus {
  status: String
  users: [User]
}

type User {
  id: ID
  name: String
  age: Int
  status: String
}
```

###### Příklad dotazu

```json
{
  usersGroupedByStatus {
    status
    users {
      id
      name
      age
    }
  }
}
```

V tomto příkladu:
- Definujeme dotaz `usersGroupedByStatus`, který vrací seznam uživatelů seskupených podle jejich statusu.
- Resolver na straně serveru provede seskupení dat podle `status` a vrátí data ve správném formátu.

### Výhody GraphQL

1. **Flexibilita dotazů**: V GraphQL si klienti mohou vybrat přesně ta data, která potřebují, což snižuje množství přenášených dat a může zlepšit výkon aplikace.

2. **Agregace dat z různých zdrojů**: GraphQL umožňuje agregovat data z různých databází nebo služeb do jednoho dotazu. To zjednodušuje vývojáře práci s více zdroji dat.

3. **Typová bezpečnost**: GraphQL schema je silně <mark style="background: #FFF3A3A6;">typované</mark>, což zajišťuje, že všechny dotazy a mutace jsou typově bezpečné. To pomáhá předcházet chybám při vývoji.

4. **Dokumentace**: GraphQL automaticky generuje dokumentaci na základě svého schématu. Klienti mohou snadno zjistit, jaké typy a dotazy jsou dostupné.

5. **Redukce over-fetchingu a under-fetchingu**: Na rozdíl od REST API, kde klienti často získávají buď příliš mnoho, nebo příliš málo dat (over-fetching, under-fetching), GraphQL umožňuje získat přesně to, co potřebujete.

### Nevýhody GraphQL

1. **Složitost serverové implementace**: Implementace GraphQL serveru může být složitější než REST API, zejména pokud se jedná o složitější schémata a vztahy mezi objekty.

2. **Nadměrná flexibilita klientů**: Přílišná flexibilita může vést k tomu, že klienti budou provádět složité a náročné dotazy, které mohou zatěžovat server a databázi.

3. **Kešování**: Kešování dat je v GraphQL složitější než v REST API. Zatímco REST využívá kešování na úrovni jednotlivých endpointů, v GraphQL je nutné implementovat kešování na úrovni jednotlivých částí dotazu.

4. **Bezpečnost**: Flexibilita dotazů může představovat bezpečnostní riziko, pokud nejsou správně nastavena oprávnění a omezení na serveru. Bezpečnostní problémy mohou vznikat také kvůli složitým dotazům, které mohou být zneužity k DoS útokům.

5. **Není vhodné pro všechny případy**: Pro jednodušší API může být REST API výhodnější a méně komplexní na implementaci. GraphQL se nejlépe hodí pro složitější systémy s různými zdroji dat a složitými vztahy.

### Závěr

GraphQL je mocný nástroj, který nabízí flexibilitu a efektivitu pro klientské aplikace. Na druhou stranu může přinést určité komplikace na serverové straně a vyžaduje pečlivé řízení dotazů a bezpečnostních mechanismů. Při rozhodování, zda použít GraphQL nebo REST API, je třeba zvážit specifické požadavky projektu.