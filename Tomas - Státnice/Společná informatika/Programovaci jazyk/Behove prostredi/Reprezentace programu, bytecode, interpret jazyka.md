---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
![[Pasted image 20240828164303.png]]
#### Reprezentace Programu
V C# je zdrojový kód překládán do meziproduktu zvaného *bytecode* (v .NET se mu říká IL - Intermediate Language). Tento bytecode je nezávislý na konkrétní platformě a běží na .NET runtime, což je virtuální stroj.

#### Bytecode (Intermediate Language - IL)
Bytecode je binární reprezentace kódu, která je platformově nezávislá. Když je C# kód zkompilován, vznikne IL, který je poté přeložen do nativního kódu přímo na cílové platformě pomocí Just-In-Time (JIT) kompilace.

**Příklad IL kódu:**
```assembly
IL_0000: ldarg.0
IL_0001: call instance void [mscorlib]System.Object::.ctor()
IL_0006: ret
```
Tento IL kód odpovídá jednoduchému konstruktoru v C#.

#### Interpret Jazyka
V .NET je interpret jazyka implementován prostřednictvím Common Language Runtime (CLR), který provádí JIT kompilaci bytecode na strojový kód, který je následně vykonán na dané platformě.

**Proces:**
1. Zdrojový kód (C#) → Překlad do IL (bytecode).
2. IL je uložen v souborech .dll nebo .exe.
3. Při spuštění CLR překládá IL do nativního strojového kódu pomocí JIT kompilace.
4. Nativní kód je vykonán procesorem.

### Shrnutí
- **Reprezentace programu**: Překlad zdrojového kódu do bytecode (IL).
- **Bytecode**: Platformově nezávislý IL, který je přeložen do strojového kódu při běhu programu.
- **Interpret jazyka (CLR)**: Provádí JIT kompilaci IL do nativního kódu.