# 28. Objektově orientované programování v PHP, knihovny třetích stran

---

### 1. Význam a princip OOP v PHP

OOP je programovací paradigma, které používá „objekty“ k reprezentaci dat a metod.

- **Třída (Class):** Předloha nebo „plán“, podle kterého se objekty vytvářejí (např. třída `Auto`).
- **Objekt (Instance):** Konkrétní věc vytvořená podle třídy (např. moje modrá Škoda).
- **Hlavní výhody:** Lepší organizace kódu, snadnější znovupoužitelnost a udržovatelnost velkých aplikací.

---

### 2. Základní syntaxe: Vlastnosti a metody

Objekt se skládá ze dvou hlavních částí:

- **Vlastnosti (Properties):** Proměnné uvnitř třídy, které uchovávají data objektu (např. `$barva`, `$rychlost`).
- **Metody (Methods):** Funkce uvnitř třídy, které definují, co objekt umí (např. `jet()`, `brzdit()`).
- **Klíčové slovo `$this`:** Používá se uvnitř třídy k odkazu na aktuální objekt (např. `$this->barva`).

---

### 3. Konstruktor a magické metody

PHP obsahuje speciální „magické“ metody, které začínají dvěma podtržítky.

- **`__construct()`:** Nejdůležitější magická metoda. Spustí se automaticky ve chvíli, kdy vytvoříš nový objekt (pomocí operátoru `new`). Slouží k nastavení počátečních hodnot.

---

### 4. Viditelnost, dědičnost a statika

Tyto pojmy určují, jak spolu třídy komunikují:

- **Viditelnost (Access Modifiers):**
    - `public`: Přístupné odkudkoliv.
    - `private`: Přístupné pouze uvnitř dané třídy.
    - `protected`: Přístupné v dané třídě a v třídách, které z ní dědí.
- **Dědičnost (`extends`):** Umožňuje jedné třídě převzít vlastnosti a metody jiné třídy. Pomáhá to neopakovat stejný kód.
- **Statické prvky (`static`):** Vlastnosti nebo metody, které patří samotné třídě, nikoliv konkrétnímu objektu. Volají se pomocí `::` (např. `Matematika::vypocti()`).

---

### 5. Knihovny, pluginy a frameworky

V moderním PHP se málokdy začíná na „zelené louce“.

- **Knihovny:** Soubory hotových tříd pro konkrétní úkoly (např. odesílání e-mailů, práce s obrázky).
- **Frameworky:** Komplexní sady nástrojů a pravidel pro tvorbu celé aplikace (např. **Nette**, **Laravel** nebo **Symfony**).
- **Composer:** Nástroj pro správu těchto knihoven (tzv. balíčkovací manažer), který zařídí jejich instalaci a aktualizaci.

---

### Praktický příklad: Jednoduchá třída

PHP

```php
<?php
class Uzivatel {
    // Vlastnosti (viditelnost private je bezpečnější)
    private $jmeno;

    // Konstruktor - nastaví jméno při vytvoření
    public function __construct($zadaneJmeno) {
        $this->jmeno = $zadaneJmeno;
    }

    // Metoda
    public function pozdrav() {
        return "Ahoj, já jsem " . $this->jmeno;
    }
}

// Vytvoření objektu (instance)
$osoba = new Uzivatel("Petr");
echo $osoba->pozdrav(); // Vypíše: Ahoj, já jsem Petr
?>
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Třída** je výkres, **objekt** je hotový dům.
- **`__construct`** se volá při `new`.
- **Zapouzdření:** Používej `private` pro data a `public` pro metody, které s nimi pracují.
- **Dědičnost:** Pomocí `extends` tvoříš specializované třídy z obecných.
- **Frameworky:** Urychlují práci a definují bezpečný standard vývoje.