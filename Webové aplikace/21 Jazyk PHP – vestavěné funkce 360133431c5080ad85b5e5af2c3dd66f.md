# 21. Jazyk PHP – vestavěné funkce

---

### 1. PHP – Popis a využití

PHP (**Hypertext Preprocessor**) je skriptovací jazyk určený primárně pro vývoj webových aplikací. 

- **Server-side:** Kód se vykonává na serveru, nikoliv v prohlížeči uživatele.
- **Dynamický obsah:** Umožňuje generovat HTML stránky na základě dat z databáze nebo vstupů od uživatele.
- **Integrace:** Skvěle spolupracuje s HTML a databázemi (zejména MySQL).

---

### 2. Základní syntaxe a proměnné

- **Zápis:** PHP kód se vkládá mezi značky `<?php` a `?>`.
- **Proměnné:** Vždy začínají znakem dolaru `$`. Jsou dynamicky typované (nemusíme předem říkat, zda jde o číslo nebo text).
- **Pole:** Klíčový prvek pro práci s daty.
    - *Indexovaná:* Přístup přes čísla (0, 1, 2...).
    - *Asociativní:* Přístup přes klíče – textové názvy (např. `$uzivatel['jmeno']`).
    - *Globální pole:* Speciální pole jako `$_GET` nebo `$_POST` pro data z formulářů.

---

### 3. Základní vestavěné funkce a konstrukce

Zde se zaměř na funkce, které tvoří "kostru" každého skriptu: 

- **Výstup:** `echo` – vypíše text nebo proměnnou přímo do HTML stránky.
- **Vkládání souborů:**
    - `include`: Vloží jiný soubor (pokud chybí, skript pokračuje s varováním).
    - `require`: Vloží jiný soubor (pokud chybí, skript se zastaví s chybou – bezpečnější pro důležité části).
- **Kontrola proměnných:**
    - `isset()`: Vrátí true, pokud proměnná existuje a není NULL.
    - `empty()`: Zkontroluje, zda je proměnná "prázdná" (obsahuje 0, prázdný řetězec, false nebo neexistuje).

---

### 4. Specializované vestavěné funkce

Při zkoušce stačí uvést 2–3 příklady z každé kategorie:

- **Práce s textem (Stringy):**
    - `strlen()`: Zjistí délku textu.
    - `explode()`: Rozseká text na pole podle určitého znaku (např. podle čárky).
    - `trim()`: Odstraní bílé znaky (mezery) ze začátku a konce textu.
- **Práce s poli:**
    - `count()`: Vrátí počet prvků v poli.
    - `sort()` / `asort()`: Seřadí pole.
    - `array_push()`: Přidá prvek na konec pole.
- **Datum a čas:**
    - `date()`: Zformátuje aktuální nebo zadaný čas do podoby textu (např. `date("d. m. Y")`).

`time()`: Vrátí aktuální čas v podobě "timestamp" (počet sekund od roku 1970). 

---

### Praktický příklad: Využití funkcí

PHP

```php
<?php
// Kontrola, zda přišlo jméno z formuláře
if (isset($_GET['jmeno']) && !empty($_GET['jmeno'])) {
    $jmeno = trim($_GET['jmeno']); // Odstraníme mezery
    echo "Ahoj, " . $jmeno . "!";
    echo " Dnes je: " . date("d.m.Y"); // Vypíšeme dnešní datum
} else {
    echo "Prosím, zadej své jméno.";
}
?>
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **PHP** běží na serveru a generuje HTML pro klienta.
- **Proměnné** začínají na `$`, příkazy končí středníkem `;`.
- **Include vs. Require:** Require je přísnější – při chybě zastaví web.
- **Isset vs. Empty:** Isset řeší existenci, Empty řeší obsah (zda tam "něco" je).
- **Pole** jsou základním úložištěm pro data, se kterými PHP pracuje pomocí funkcí jako `count` nebo `sort`.