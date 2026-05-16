# 7. Struktura, union, výčet v jazyce C

---

### 1. Struktura (`struct`)

Struktura je uživatelsky definovaný datový typ, který umožňuje seskupit různé (i různorodé) datové typy pod jedno společné jméno. Jednotlivým prvkům uvnitř struktury říkáme **položky** nebo **členy**.

- **Využití:** Pro reprezentaci reálných objektů (např. student má jméno, věk a průměr).
- **Paměť:** Velikost struktury v paměti je dána součtem velikostí všech jejích položek (plus případné zarovnání procesorem). Všechny položky existují v paměti **současně** vedle sebe.
- **Přístup k položkám:** Používáme operátor tečka `.` (pro proměnné) nebo šipku `>` (pro pointery na strukturu).

### 2. Union (`union`)

Union (sjednocení) vypadá na první pohled stejně jako struktura, ale funguje v paměti úplně jinak.

- **Hlavní vlastnost:** Všechny položky unionu sdílejí **stejné místo v paměti**.
- **Paměť:** Velikost unionu je dána velikostí jeho **největší položky**.
- **Omezení:** V jeden okamžik můžeme smysluplně pracovat pouze s **jednou** položkou. Změna jedné položky přepíše hodnotu ostatních.
- **Využití:** Šetření pamětí nebo v situacích, kdy víme, že objekt může být buď typ A, nebo typ B, ale nikdy obojí najednou.

### 3. Výčtový typ (`enum`)

Výčtový typ slouží k definování množiny pojmenovaných celočíselných konstant.

- **Význam:** Zvyšuje čitelnost a přehlednost kódu (místo čísla 0 použijeme slovo `PONDELI`).
- **Hodnoty:** Překladač automaticky přiřazuje položkám celá čísla začínající od 0 (pokud neurčíme jinak).

---

### Praktická ukázka v kódu

**Definice a práce se strukturou a výčtem:**

```c
#include <stdio.h>

// Definice výčtového typu
enum Barva { CERVENA, ZELENA, MODRA }; // 0, 1, 2

// Definice struktury pomocí typedef (pro snazší zápis)
typedef struct {
    char znacka[20];
    int rok_vyroby;
    enum Barva barva_auta;
} AUTO;

int main() {
    AUTO mojeAuto = {"Skoda", 2020, ZELENA}; // Inicializace

    printf("Auto: %s, Rok: %d\n", mojeAuto.znacka, mojeAuto.rok_vyroby);
    
    if (mojeAuto.barva_auta == ZELENA) {
        printf("Auto je zelene.");
    }

    return 0;
}
```

**Ukázka unionu (rozdíl v paměti):**

```c
union Data {
    int i;
    float f;
};

// ... v main ...
union Data d;
d.i = 10;
d.f = 5.5; // Tímto se hodnota 'i' přepsala/pobořila, protože sdílejí stejné místo!
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Struktura (`struct`):** Položky jsou v paměti **za sebou**, velikost je jejich součet. Vhodné pro záznamy (např. v databázi).
- **Union (`union`):** Položky jsou v paměti **přes sebe**, velikost je podle největší položky. Šetří paměť.
- **Výčet (`enum`):** Sada pojmenovaných konstant (zástupná jména za čísla).
- **Typedef:** Často se používá k tomu, abychom nemuseli psát `struct MojeStruktura s;`, ale stačilo jen `MojeStruktura s;`.
- **Operátory:** Tečka `.` pro přímý přístup, šipka `>` pokud pracujeme s pointerem na strukturu.