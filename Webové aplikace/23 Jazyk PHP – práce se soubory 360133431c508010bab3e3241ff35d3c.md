# 23. Jazyk PHP – práce se soubory

---

### 1. Procházení souborů a adresářů na serveru

PHP umožňuje aplikaci číst obsah složek a ověřovat stav souborů na disku serveru. 

- **`file_exists()`**: Zjistí, zda daný soubor nebo složka vůbec existuje.
- **`mkdir()`**: Vytvoří nový adresář (složku).
- **`glob()`**: Velmi užitečná funkce, která vyhledá soubory podle masky (např. `glob("*.jpg")` vrátí pole všech obrázků ve složce).
- **Práce s obsahem složky**: Klasický postup využívá funkce `opendir()` (otevření), `readdir()` (čtení po jednom souboru) a `closedir()` (zavření).

---

### 2. Nahrávání souborů (Upload) – Princip a příprava

Aby uživatel mohl soubor odeslat, musí být splněny tři základní podmínky v HTML formuláři: 

1. **Metoda POST**: Soubory nelze posílat metodou GET. 
2. **Atribut `enctype="multipart/form-data"`**: Bez tohoto nastavení prohlížeč pošle pouze jméno souboru, nikoliv jeho obsah. 
3. **Prvek `<input type="file">`**: Vytvoří v prohlížeči tlačítko pro výběr souboru. 

Na straně serveru existují omezení (v souboru `php.ini`), jako je **`upload_max_filesize`** (maximální velikost souboru) nebo **`post_max_size`** (maximální objem dat odeslaných najednou). 

---

### 3. Superglobální pole `$_FILES`

Jakmile soubor dorazí na server, PHP ho uloží do dočasné složky a informace o něm vloží do pole `$_FILES`. Každý soubor v tomto poli má 5 klíčů: 

- **`['name']`**: Původní název souboru z počítače uživatele.
- **`['type']`**: MIME typ souboru (např. `image/jpeg`).
- **`['size']`**: Velikost souboru v bajtech.
- **`['tmp_name']`**: Cesta k dočasnému souboru na serveru (odtud ho musíme přesunout).
- **`['error']`**: Chybový kód (0 znamená, že se nahrávání povedlo).

---

### 4. Zpracování uploadu v PHP

K bezpečnému uložení souboru slouží vestavěné funkce: 

- **`is_uploaded_file()`**: Ověří, zda byl soubor skutečně nahrán přes HTTP POST (bezpečnostní pojistka).
- **`move_uploaded_file()`**: Přesune soubor z dočasného umístění do námi zvolené složky (např. do `uploads/`).

---

### Praktický příklad: Jednoduchý upload obrázku

PHP

```php
<?php
// Kontrola, zda byl odeslán formulář a zda neobsahuje chyby
if (isset($_FILES['obrazek']) && $_FILES['obrazek']['error'] === 0) {
    
    $cilovaSlozka = "uploads/";
    $nazevSouboru = $_FILES['obrazek']['name'];
    $docasnaCesta = $_FILES['obrazek']['tmp_name'];

    // Sestavení finální cesty k souboru
    $cil = $cilovaSlozka . basename($nazevSouboru);

    // Přesun souboru z dočasné složky do cílové
    if (move_uploaded_file($docasnaCesta, $cil)) {
        echo "Soubor byl úspěšně nahrán do: " . $cil;
    } else {
        echo "Při nahrávání došlo k chybě.";
    }
}
?>
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **HTML formulář:** Musí mít `method="post"` a `enctype="multipart/form-data"`.
- **Dočasné úložiště:** PHP soubor nejdříve nahraje do dočasné složky (`tmp_name`), odkud ho musíme přesunout.
- **Pole `$_FILES`:** Obsahuje všechna metadata o souboru (název, velikost, typ, chyby).
- **Funkce `move_uploaded_file`:** Nejdůležitější funkce pro uložení souboru na server.
- **Bezpečnost:** Vždy je dobré kontrolovat příponu souboru a jeho velikost, aby nám uživatel nenahrál např. nebezpečný script.