# 25. Jazyk PHP – autentizace uživatelů

---

### 1. Autentizace – význam a princip

Autentizace je proces **ověření identity** uživatele (zda je uživatel skutečně tím, za koho se vydává).

- **Princip:** Uživatel zadá své přihlašovací údaje (obvykle jméno/e-mail a heslo) do formuláře.
- **Porovnání:** Skript na serveru přijme tato data a porovná je s údaji uloženými v databázi.
- **Výsledek:** Pokud se údaje shodují, je uživatel považován za autentizovaného a aplikace mu vytvoří „relaci“ (session).

---

### 2. Session (Relace) v PHP

Problémem protokolu HTTP je, že je „bezstavový“ – server po odeslání stránky „zapomene“, kdo s ním mluvil. K vyřešení tohoto problému slouží **Session**.

- **Princip fungování:** * Při zahájení relace server vytvoří unikátní ID (Session ID).
    - Toto ID se uloží do prohlížeče uživatele (obvykle jako cookie s názvem `PHPSESSID`).
    - Samotná data (např. informace o tom, že je uživatel „Admin“) zůstávají uložena **na serveru**.
    - Při každém dalším požadavku prohlížeč pošle Session ID a server si podle něj dohledá data daného uživatele.

---

### 3. Funkce a pole pro práci se Session

V PHP pracujeme se session pomocí vestavěných nástrojů:

- **`session_start()`**: Naprosto klíčová funkce, která musí být zavolána na **úplném začátku** skriptu (před jakýmkoliv výstupem do HTML). Buď novou session vytvoří, nebo naváže na existující.
- **`$_SESSION`**: Globální asociativní pole, do kterého ukládáme data, která si chceme pamatovat napříč stránkami (např. `$_SESSION['user_id'] = 5;`).
- **`unset($_SESSION['polozka'])`**: Odstraní konkrétní údaj ze session (vhodné pro odhlášení určité části dat).
- **`session_destroy()`**: Zcela zruší celou aktuální session (typicky při odhlášení uživatele).

---

### 4. Využití databáze a ukládání hesel

Databáze hraje při autentizaci roli trvalého úložiště.

- **Tabulka uživatelů:** Obsahuje minimálně sloupce pro login a heslo.
- **Bezpečnost hesel:** U maturity je důležité zmínit, že hesla se **nikdy nesmí ukládat v čitelné podobě**.
- **Hashování:** Hesla se ukládají jako tzv. „hashe“ (pomocí funkcí jako `password_hash()`). Při přihlášení se pak zadané heslo porovná s hashem v databázi pomocí `password_verify()`.

---

### Praktický příklad: Jednoduchý login skript

PHP

```php
<?php
session_start(); // 1. Zahájení session na začátku souboru 

// Simulace ověření údajů (v praxi by zde byl dotaz do DB) 
$uzivatel_z_db = "admin";
$heslo_hash_z_db = password_hash("tajneheslo", PASSWORD_DEFAULT);

if (isset($_POST['login'])) {
    $jmeno = $_POST['username'];
    $heslo = $_POST['password'];

    // 2. Ověření jména a hesla 
    if ($jmeno === $uzivatel_z_db && password_verify($heslo, $heslo_hash_z_db)) {
        // 3. Uložení stavu do pole $_SESSION 
        $_SESSION['prihlasen'] = true;
        $_SESSION['uzivatel'] = $jmeno;
        echo "Přihlášení úspěšné!";
    } else {
        echo "Chybné jméno nebo heslo.";
    }
}
?>
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Autentizace** = ověření identity (kdo jsi); **Session** = udržení stavu (pamatuji si tě).
- **`session_start()`** musí být v kódu jako první.
- Data session jsou na **serveru**, u klienta je jen **ID relace** v cookie.
- Hesla do databáze patří pouze v **hashované podobě** kvůli bezpečnosti.
- Pro odhlášení se používá **`session_destroy()`** nebo smazání klíče z **`$_SESSION`**.