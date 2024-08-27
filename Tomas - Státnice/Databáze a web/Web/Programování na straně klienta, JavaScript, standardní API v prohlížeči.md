---
tags: web,tomas,databaze_a_web
dg-publish: true
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT
#### 1. Napsat klientský kód (JavaScript), který v reakci na událost provede dotaz na server, zpracuje odpověď a modifikuje DOM

V tomto příkladu si ukážeme jednoduchý JavaScriptový kód, který po kliknutí na tlačítko provede dotaz na server (např. pomocí `fetch` API), zpracuje odpověď (např. v JSON formátu) a modifikuje DOM (Document Object Model).

```html
<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Příklad API volání</title>
</head>
<body>
    <button id="fetchData">Načíst data</button>
    <div id="output"></div>

    <script>
        document.getElementById('fetchData').addEventListener('click', function() {
            fetch('https://jsonplaceholder.typicode.com/posts/1')
                .then(response => response.json())
                .then(data => {
                    const outputDiv = document.getElementById('output');
                    outputDiv.innerHTML = `<h3>${data.title}</h3><p>${data.body}</p>`;
                })
                .catch(error => console.error('Chyba při načítání dat:', error));
        });
    </script>
</body>
</html>
```

Tento kód nejprve přidá posluchače události (event listener) na tlačítko s ID `fetchData`. Po kliknutí na tlačítko se provede HTTP GET dotaz na server pomocí `fetch` API. Odpověď zpracujeme jako JSON a následně vložíme data do divu s ID `output`.

#### 2. Příklady standardních API dostupných v prohlížeči

V prohlížeči je k dispozici mnoho standardních API, které můžete využít. Zde jsou některé z nejběžnějších:

- **DOM API**: Umožňuje manipulaci s DOM (Document Object Model). Například `document.querySelector`, `document.createElement`, `element.addEventListener` atd.
- **Fetch API**: Slouží pro asynchronní volání na server (pro načítání zdrojů, API volání atd.). 
- **LocalStorage API**: Umožňuje ukládání dat na straně klienta (v prohlížeči) pomocí `localStorage.setItem`, `localStorage.getItem`.
- **Geolocation API**: Poskytuje přístup k aktuální geografické poloze zařízení (pokud to uživatel povolí).
- **Canvas API**: Používá se pro kreslení grafiky na webové stránky pomocí elementu `<canvas>`.
- **WebSockets API**: Umožňuje komunikaci mezi klientem a serverem v reálném čase.

#### 3. Vysvětlit a použít mechanizmy pro asynchronní programování v JavaScriptu: Callbacks, Promises, Async/Await, Event Loop

**Asynchronní programování** je klíčové pro JavaScript, protože umožňuje vykonávání úloh, aniž by byl blokován hlavní vlákno (což je důležité pro interaktivní aplikace).

##### Callbacks

Callbacks jsou funkce, které jsou předány jako argumenty jiným funkcím a jsou vykonány po dokončení asynchronní operace.

```javascript
function getData(callback) {
    setTimeout(() => {
        callback("Data načtena!");
    }, 1000);
}

getData(function(message) {
    console.log(message);  // "Data načtena!" po jedné sekundě
});
```

##### Promises

Promises jsou novější způsob, jak pracovat s asynchronními operacemi. Umožňují lepší práci s více asynchronními operacemi a lepší čitelnost kódu.

```javascript
function getData() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            resolve("Data načtena!");
        }, 1000);
    });
}

getData()
    .then(message => console.log(message))  // "Data načtena!" po jedné sekundě
    .catch(error => console.error(error));
```

##### Async/Await

Async/Await je syntaktický cukr nad Promises, který umožňuje psát asynchronní kód podobně jako synchronní kód, což výrazně zvyšuje čitelnost.

```javascript
async function fetchData() {
    try {
        let message = await getData();
        console.log(message);  // "Data načtena!" po jedné sekundě
    } catch (error) {
        console.error(error);
    }
}

fetchData();
```

##### Event Loop

Event Loop je mechanismus v JavaScriptu, který umožňuje asynchronní operace a zajišťuje, že úlohy jsou vykonávány ve správném pořadí. Funguje tak, že hlavní vlákno prochází frontou úloh (callbacků) a vykonává je, když jsou dostupné.

Event Loop zajišťuje, že například po dokončení asynchronní operace (jako je načtení dat z API) bude příslušná callback funkce vykonána, aniž by blokovala běh jiných částí kódu.

V kombinaci tyto techniky umožňují efektivní a škálovatelné asynchronní programování v JavaScriptu, což je klíčové pro moderní webové aplikace.
![[Pasted image 20240816203550.png]]