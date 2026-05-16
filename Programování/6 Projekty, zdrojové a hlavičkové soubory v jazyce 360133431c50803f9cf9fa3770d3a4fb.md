# 6. Projekty, zdrojové a hlavičkové soubory v jazyce

---

### 1. Projekty v jazyce C (Modularizace)

Většina reálných programů se neskládá z jednoho souboru, ale z mnoha menších částí. Tomu říkáme **modularizace**.

- **Důvody:** Lepší přehlednost kódu, snadnější hledání chyb a možnost znovu použít hotové moduly v jiných projektech.
- **Projekt:** Je soubor instrukcí pro vývojové prostředí (IDE), který říká, které soubory k programu patří a jak se mají společně přeložit.

### 2. Zdrojové vs. Hlavičkové soubory

V jazyce C rozlišujeme dva základní typy souborů:

- **Zdrojové soubory (`.c`):**
    - Obsahují samotnou **implementaci** (těla funkcí, logiku programu).
    - Jsou to soubory, které překladač skutečně zpracovává.
- **Hlavičkové soubory (`.h`):**
    - Slouží jako „obsah“ nebo rozhraní (interface).
    - Obsahují pouze **deklarace** (prototypy funkcí, definice datových typů, konstanty a makra).
    - Vkládají se do zdrojových souborů pomocí direktivy `#include "soubor.h"`.

### 3. Stavba vlastního hlavičkového souboru

Abychom zabránili chybám při vícenásobném vložení stejného hlavičkového souboru (což by vedlo k chybě redefinice), používáme tzv. **podmíněný překlad** (Header Guards).

**Struktura souboru `moje_funkce.h`:**

```c
#ifndef MOJE_FUNKCE_H   // Pokud není definováno...
#define MOJE_FUNKCE_H   // ...tak definuj

// Zde jsou deklarace (prototypy)
int secti(int a, int b);
void pozdrav();

#endif // Konec ochrany
```

### 4. Spojování a překlad programu

Proces vzniku spustitelného programu (`.exe`) má několik fází:

1. **Preprocesor:** Zpracuje direktivy `#include` (vloží text hlaviček) a `#define` (nahradí makra).
2. **Kompilátor (Překladač):** Přeloží každý zdrojový soubor zvlášť do strojového kódu. Vznikají tzv. **objektové soubory** s příponou `.obj` (nebo `.o`).
3. **Linker (Spojovač):** Vezme všechny `.obj` soubory a přidá k nim kód z knihoven (např. `stdio.h`). Vše spojí do jednoho výsledného souboru `.exe`.

---

### Praktický příklad: Projekt o dvou souborech

**Soubor `vypocty.c` (Implementace):**

```c
#include "vypocty.h"

int zdvojnasob(int x) {
    return x * 2;
}
```

**Soubor `main.c` (Hlavní program):**

```c
#include <stdio.h>
#include "vypocty.h" // Vložení vlastního hlavičkového souboru

int main() {
    int cislo = 5;
    printf("Vysledek: %d", zdvojnasob(cislo));
    return 0;
}
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Hlavičkový soubor (`.h`)** = deklarace (slib, že funkce existuje).
- **Zdrojový soubor (`.c`)** = definice (skutečný kód funkce).
- **`#include <stdio.h>`** vs **`#include "moje.h"`**: Špičaté závorky jsou pro systémové knihovny, uvozovky pro soubory v aktuální složce projektu.
- **Header Guards (`#ifndef ...`)**: Jsou povinné v každém `.h` souboru, aby se program „nepohádal“ při vkládání.
- **Linker** je ten, kdo dává dílky skládačky dohromady do výsledného souboru.