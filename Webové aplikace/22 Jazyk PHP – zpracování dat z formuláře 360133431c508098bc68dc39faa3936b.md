# 22. Jazyk PHP – zpracování dat z formuláře

---

### 1. Metody odesílání dat (GET vs. POST)

Při odesílání dat z formuláře hraje klíčovou roli atribut `method` v HTML značce `<form>`.

| **Vlastnost** | **Metoda GET** | **Metoda POST** |
| --- | --- | --- |
| **Viditelnost** | Data jsou vidět v URL adrese (za otazníkem). | Data jsou skrytá v těle HTTP požadavku. |
| **Kapacita** | Omezená délka (cca 2000 znaků). | Téměř neomezená velikost dat. |
| **Bezpečnost** | Nevhodná pro hesla a citlivé údaje. | Bezpečnější (údaje nejsou vidět v historii prohlížeče). |
| **Využití** | Vyhledávání, filtrování, řazení (lze uložit do záložek). | Přihlašování, registrace, odesílání velkých textů. |

---

### 2. Globální pole (Superglobály)

V PHP k datům přistupujeme přes tzv. superglobální pole, což jsou asociativní pole, která PHP automaticky naplní podle použité metody:

- **`$_GET`**: Obsahuje data odeslaná metodou GET. Klíčem v poli je hodnota atributu `name` z HTML.
- **`$_POST`**: Obsahuje data odeslaná metodou POST. Opět využívá atribut `name` jako klíč.
- **`$_FILES`**: Speciální pole určené pro nahrávané soubory (vyžaduje `enctype="multipart/form-data"` ve formuláři).

---

### 3. Základní funkce pro zpracování

Než začneme s daty pracovat, musíme ověřit jejich existenci a obsah, abychom předešli chybám.

- **`isset($_POST['tlacitko'])`**: Zjišťuje, zda byl formulář vůbec odeslán (zda existuje klíč v poli).
- **`empty($promenna)`**: Kontroluje, zda uživatel do pole něco napsal. Za prázdné se považuje i `0` nebo prázdný řetězec.
- **`htmlspecialchars()`**: **Důležité u maturity!** Tato funkce převádí speciální znaky (jako `<` nebo `>`) na entity. Slouží jako základní ochrana proti útoku **XSS** (vložení škodlivého skriptu do stránky).

---

### Praktický příklad: Zpracování formuláře

U zkoušky ti může být zadán úkol typu: „Napište skript, který přijme jméno a vypíše ho.“

PHP

```php
<?php
// 1. Ověříme, zda byl formulář odeslán metodou POST
if (isset($_POST['odeslat'])) {
    
    // 2. Ověříme, zda není pole se jménem prázdné
    if (!empty($_POST['jmeno'])) {
        
        // 3. Ošetříme vstup proti XSS a uložíme do proměnné
        $jmeno = htmlspecialchars($_POST['jmeno']);
        
        echo "Vítejte, uživateli " . $jmeno;
    } else {
        echo "Chyba: Jméno musí být vyplněno!";
    }
}
?>
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **GET** dává data do URL (vhodné pro vyhledávače), **POST** do těla požadavku (vhodné pro hesla).
- V PHP odpovídají metodám pole **`$_GET`** a **`$_POST`**.
- Klíčem v asociativním poli PHP je vždy atribut **`name`** z HTML prvku.
- Před prací s daty vždy použij **`isset()`** a **`empty()`** pro kontrolu.
- Nikdy nevypisuj uživatelská data bez **`htmlspecialchars()`**, jinak riskuješ bezpečnostní díru (XSS).