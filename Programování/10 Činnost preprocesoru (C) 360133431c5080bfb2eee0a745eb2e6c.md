# 10. Činnost preprocesoru (C)

---

### 1. Charakteristika činnosti preprocesoru

Preprocesor je program, který se automaticky spouští jako první krok při překladu zdrojového kódu.

- **Vstup:** Soubor se zdrojovým kódem (`.c`).
- **Výstup:** Upravený textový soubor (tzv. rozvinutý zdrojový kód), který pak putuje do kompilátoru.
- **Zápis:** Všechny příkazy pro preprocesor (direktivy) začínají znakem křížku **`#`** a nejsou zakončeny středníkem.

### 2. Tvorba maker (`#define`)

Makra slouží k nahrazování textu v kódu.

- **Symbolické konstanty:** Místo „magických čísel“ používáme jména.
    - `#define PI 3.14159` – preprocesor všude v kódu přepíše slovo `PI` na dané číslo.
- **Makra s parametry:** Vypadají jako funkce, ale fungují jinak.
    - `#define NA_DRUHOU(x) ((x) * (x))`

### Srovnání makra a funkce:

| **Vlastnost** | **Makro (#define)** | **Funkce (void, int, ...)** |
| --- | --- | --- |
| **Zpracování** | Textové nahrazení před překladem. | Skutečný skok v programu během běhu. |
| **Rychlost** | Rychlejší (odpadá režie volání funkce). | Pomalejší (práce se zásobníkem). |
| **Bezpečnost** | Nebezpečné (nekontroluje datové typy). | Bezpečné (překladač hlídá typy). |
| **Velikost** | Zvětšuje kód (text se vkládá opakovaně). | Menší kód (funkce je v paměti jen jednou). |

### 3. Podmíněný překlad

Umožňuje překladači říct, které části kódu má zpracovat a které má ignorovat. To je užitečné pro programy běžící na různých operačních systémech nebo pro ladění.

- **Direktivy:** `#if`, `#ifdef` (je-li definováno), `#ifndef` (není-li definováno), `#else`, `#endif`.
- **Typické využití:** Ochrana hlavičkových souborů (tzv. Header Guards), aby nedošlo k jejich vícenásobnému vložení.

### 4. Hlavičkové soubory (`#include`)

Direktiva `#include` vloží celý obsah zadaného souboru do místa, kde je napsána.

- **`#include <soubor.h>`**: Preprocesor hledá soubor v systémových adresářích knihoven (standardní knihovny jako `stdio.h`).
- **`#include "soubor.h"`**: Preprocesor hledá soubor nejdříve v aktuálním adresáři projektu (vlastní hlavičkové soubory).

---

### Praktický příklad: Header Guards a Makro

**Soubor `vypocty.h`:**

```c
#ifndef VYPOCTY_H  // Podmíněný překlad: Pokud není VYPOCTY_H definováno
#define VYPOCTY_H  // tak ho definuj

#define MAX_HODNOTA 100 // Symbolická konstanta

// Makro pro maximum ze dvou čísel
#define MAX(a,b) (((a) > (b)) ? (a) : (b))

#endif
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Preprocesor** = textový procesor před kompilací.
- **Direktivy** začínají na `#` (include, define, ifndef).
- **Makra** jsou rychlá, ale „hloupá“ (neznají typy).
- **Podmíněný překlad** šetří práci tím, že vynechává nepotřebné části kódu.
- **Hlavičkové soubory** propojují deklarace s vaším kódem.