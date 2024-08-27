---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě poznamek z DI.
### Digitální certifikát a jeho použití
![[Pasted image 20240825144842.png]]
#### Co je digitální certifikát?
Digitální certifikát je veřejné prohlášení, které **potvrzuje vlastnictví soukromého klíče**. Slouží k tomu, aby třetím stranám poskytl důvěru v autenticitu určité osoby nebo entity, která používá tento klíč pro zabezpečenou komunikaci. Certifikát tedy spojuje identitu držitele s odpovídajícím veřejným klíčem a je vydáván certifikační autoritou (CA), která ověřuje, že veřejný klíč patří danému subjektu.

#### Základní vlastnosti digitálního certifikátu:
- **Veřejný klíč**: Obsahuje veřejný klíč, který je spojen s identitou držitele certifikátu.
- **Certifikační autorita (CA)**: Důvěryhodná třetí strana, která vydává certifikát po ověření totožnosti držitele.
- **Doba platnosti**: Certifikát má omezenou dobu platnosti, po jejímž uplynutí je třeba jej obnovit.
- **Digitální podpis CA**: Certifikační autorita digitálně podepisuje certifikát, což zaručuje jeho pravost a důvěryhodnost.

#### Použití digitálního certifikátu:
1. **Šifrování komunikace**: Digitální certifikáty se běžně používají v kombinaci s protokoly SSL/TLS, které zajišťují šifrovanou komunikaci mezi webovým serverem a prohlížečem. Například v HTTPS komunikaci webový server poskytuje svůj certifikát pro ověření své identity klientovi (prohlížeči).

2. **Digitální podpisy**: Certifikáty se také používají k vytváření digitálních podpisů, které zajišťují autenticitu a integritu dokumentů. Při podepisování dokumentu se použije soukromý klíč, který je spojen s certifikátem. Příjemce pak může ověřit pravost podpisu pomocí veřejného klíče obsaženého v certifikátu.

3. **Autentizace uživatelů**: V prostředí veřejné klíčové infrastruktury (PKI) mohou být digitální certifikáty použity k autentizaci uživatelů při přihlašování do systémů nebo přístupu k citlivým informacím.

4. **Řetězec důvěry**: Certifikační autority vytvářejí řetězec důvěry, kdy hlavní (kořenové) autority jsou důvěryhodné a jejich certifikáty jsou integrovány do operačních systémů nebo prohlížečů. Certifikáty vydané těmito autoritami jsou pak automaticky důvěryhodné pro všechny uživatele těchto systémů.

Shrnutím lze říci, že digitální certifikát hraje klíčovou roli při zajištění bezpečnosti a důvěryhodnosti online komunikace, autentizace a digitálního podepisování dokumentů.