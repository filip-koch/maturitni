# 5. Proměnné v jazyce C

---

### 1. Definice a deklarace proměnné

- **Proměnná** je pojmenované místo v paměti, kam si program ukládá data určitého typu.
- **Deklarace:** Oznámení překladači, jakého jména a typu proměnná bude (např. `int cislo;`).
- **Definice:** Okamžik, kdy se pro proměnnou skutečně vyhradí místo v paměti (v C většinou splývá s deklarací).
- **Inicializace:** První přiřazení hodnoty do proměnné (např. `int a = 5;`).

### 2. Rozsah platnosti proměnných (Scope)

U zkoušky je nejdůležitější rozlišit, kde v kódu proměnná „žije“:

### A) Lokální proměnné

- Jsou definovány **uvnitř funkce** nebo bloku `{ }`.
- Vznikají při vstupu do bloku a zanikají při jeho opuštění.
- Jsou uloženy v paměti typu **zásobník (stack)**.
- **Pozor:** Nejsou automaticky nulovány – po vytvoření v nich může být „smetí“ (náhodná data).

### B) Globální proměnné

- Jsou definovány **vně všech funkcí** (obvykle na začátku souboru).
- Jsou přístupné z jakéhokoli místa v celém souboru (případně i v jiných souborech).
- Existují po celou dobu běhu programu.
- Při startu programu jsou automaticky nulovány.
- *Doporučení:* U maturity zmiň, že globálními proměnnými by se mělo šetřit, protože znepřehledňují kód.

### 3. Paměťové třídy v jazyce C

Určují viditelnost a dobu života (existenci) proměnné:

1. **`auto`**: Výchozí pro lokální proměnné (klíčové slovo se téměř nepoužívá).
2. **`static`**:
    - U lokální proměnné: Proměnná nezanikne po skončení funkce, ale **uchová si svou hodnotu** pro příští zavolání. Inicializuje se jen jednou.
    - U globální proměnné: Omezí její viditelnost pouze na ten soubor, ve kterém je definována.
3. **`extern`**: Používá se pro přístup k proměnné, která je definována v jiném zdrojovém souboru (důležité pro velké projekty).
4. **`register`**: Prosba překladači, aby proměnnou uložil přímo v registru procesoru místo v RAM (pro zrychlení), dnes už to moderní překladače dělají automaticky.

---

### Praktický příklad: Rozdíl mezi lokální, globální a statickou proměnnou

```c
#include <stdio.h>

int globalni = 10; // Globální - vidí ji všichni

void pokus() {
    int lokalni = 0;        // Lokální - vznikne znovu při každém volání
    static int staticka = 0; // Statická - hodnotu si pamatuje

    lokalni++;
    staticka++;

    printf("Lokalni: %d, Staticka: %d\n", lokalni, staticka);
}

int main() {
    pokus(); // Vypíše: Lokalni: 1, Staticka: 1
    pokus(); // Vypíše: Lokalni: 1, Staticka: 2
    return 0;
}
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Lokální proměnná:** Žije v `{ }`, po skončení bloku umírá. Je na zásobníku.
- **Globální proměnná:** Žije všude, od začátku do konce programu. Je v datovém segmentu.
- **Klíčové slovo `static`:** Způsobí, že lokální proměnná "nezapomene" svou hodnotu.
- **Klíčové slovo `extern`:** "Hele, tahle proměnná je v jiném souboru, hledej ji tam".
- **Inicializace:** Nezapomínej, že lokální proměnné musíš v C inicializovat sám, jinak obsahují náhodné hodnoty.