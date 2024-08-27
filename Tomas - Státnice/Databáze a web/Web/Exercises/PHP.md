---
dg-publish: true
tags:
  - tomas
  - web
  - databaze_a_web
---
## Jednoduchá PHP stránka s HTTP wrapperem a připojením k SQL databázi

Níže je jednoduchý příklad PHP stránky, která se připojuje k SQL databázi, načítá data a zobrazuje je na webové stránce.

### Příklad PHP stránky

```php
<?php
// Připojení k databázi
$dsn = 'mysql:host=localhost;dbname=testdb;charset=utf8';
$username = 'root';
$password = '';

try {
    $pdo = new PDO($dsn, $username, $password);
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e) {
    echo 'Chyba při připojení k databázi: ' . $e->getMessage();
    exit();
}

// Dotaz do databáze
$sql = "SELECT id, name, email FROM users";
$stmt = $pdo->query($sql);

// Výstup dat na stránku
?>
<!DOCTYPE html>
<html>
<head>
    <title>Seznam uživatelů</title>
</head>
<body>
    <h1>Seznam uživatelů</h1>
    <table border="1">
        <tr>
            <th>ID</th>
            <th>Jméno</th>
            <th>Email</th>
        </tr>
        <?php while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) : ?>
        <tr>
            <td><?php echo htmlspecialchars($row['id']); ?></td>
            <td><?php echo htmlspecialchars($row['name']); ?></td>
            <td><?php echo htmlspecialchars($row['email']); ?></td>
        </tr>
        <?php endwhile; ?>
    </table>
</body>
</html>
```

### Vysvětlení:
- **PDO**: Používáme PDO (PHP Data Objects) pro připojení k MySQL databázi a provádění SQL dotazů. PDO je výhodné pro své schopnosti pracovat s více typy databází a pro zabudovanou podporu prevence SQL injekcí.
- **HTTP Wrapper**: Tento kód přímo neukazuje použití HTTP wrapperu, ale kdybychom chtěli načítat obsah z URL, mohli bychom využít funkce jako `file_get_contents()`.
- **Tabulka**: Data získaná z SQL dotazu jsou dynamicky vkládána do HTML tabulky.

Tento jednoduchý příklad ukazuje základní principy PHP programování, které můžete rozšířit o složitější funkcionality, jako jsou uživatelské relace nebo zpracování formulářů.

## PHP Interleaving

**PHP Interleaving** znamená střídání mezi HTML a PHP kódem ve stejném souboru. To umožňuje dynamické generování obsahu.

```php
<!DOCTYPE html>
<html>
<head>
    <title>Příklad PHP interleaving</title>
</head>
<body>
    <h1>Vítejte na mé stránce</h1>
    <p>Dnešní datum a čas je: 
        <?php 
            echo date('d.m.Y H:i:s'); 
        ?>
    </p>
    <p>
        <?php
            $hour = date('H');
            if ($hour < 12) {
                echo "Dobré ráno!";
            } elseif ($hour < 18) {
                echo "Dobré odpoledne!";
            } else {
                echo "Dobrý večer!";
            }
        ?>
    </p>
</body>
</html>
```

V tomto příkladu se střídá HTML a PHP kód, kde PHP generuje dynamický obsah na základě aktuálního času.