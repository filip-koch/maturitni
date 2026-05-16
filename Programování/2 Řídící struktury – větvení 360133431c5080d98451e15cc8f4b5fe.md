# 2. Řídící struktury – větvení

---

### 1. Charakteristika větvení

Větvení (nebo také podmíněný příkaz) je řídící struktura, která umožňuje provést různé části kódu v závislosti na splnění nebo nesplnění určité podmínky. Podmínka je vždy **logický výraz**, jehož výsledkem je buď pravda (`true` / nenulová hodnota), nebo nepravda (`false` / nula).

### 2. Typy podmíněných příkazů

U zkoušky rozlišujeme tři základní situace:

### A) Neúplné větvení (Jednoduchý `if`)

Provádí akci pouze tehdy, je-li podmínka splněna. Pokud splněna není, program pokračuje dál bez jakékoli akce.

- **Příklad:** Pokud prší, vezmi si deštník.

### B) Úplné větvení (`if-else`)

Program má připraveny dvě varianty. Jedna se provede při splnění podmínky, druhá (větev `else`) při jejím nesplnění.

- **Příklad:** Pokud máš lístek, jdi do kina, jinak jdi domů.

### C) Mnohonásobné větvení (`switch` / `case`)

Používá se v situacích, kdy proměnná může nabývat mnoha konkrétních hodnot (např. výběr z menu 1, 2, 3) a pro každou chceme jinou reakci. Je to přehlednější než psát mnoho `if` za sebou.

### 3. Grafický zápis (Vývojové diagramy)

V grafickém zápisu používáme pro větvení **kosočtverec**.

- Z kosočtverce vedou vždy dva směry označené **+ / -** (nebo **Ano / Ne**, **True / False**).
- U `switch` může z jednoho bodu vést více čar k jednotlivým hodnotám.

### 4. Zápis v jazyce C a Java

Syntaxe je v obou jazycích téměř identická, což je pro tebe u maturity velká výhoda.

**Příklad `if-else` (v C i Javě):**

C

```c
// Kontrola věku pro vstup
int vek = 18;

if (vek >= 18) {
    // Provede se, pokud je podmínka PRAVDA
    printf("Vstup povolen.\n"); 
} else {
    // Provede se, pokud je podmínka NEPRAVDA
    printf("Vstup zakázán.\n");
}
```

**Příklad `switch` (v C i Javě):**

C

```c
int volba = 2;

switch (volba) {
    case 1:
        printf("Vybral jsi jedničku.");
        break; // Důležité! Ukončí switch, aby program nepokračoval do další case.
    case 2:
        printf("Vybral jsi dvojku.");
        break;
    default:
        // Provede se, pokud žádná z možností výše nesouhlasí
        printf("Neplatná volba.");
}
```

### 5. Ternární operátor (Bonus pro lepší známku)

Pokud chceš zapůsobit, zmiň existenci ternárního operátoru `? :`. Je to zkrácený zápis `if-else` do jednoho řádku.

```c
vysledek = (podmínka) ? hodnota_pokud_ano : hodnota_pokud_ne;
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Logický výraz:** Základ každé podmínky (výsledek 1/0 nebo true/false).
- **Relační operátory:** `==` (rovná se), `!=` (nerovná se), `>`, `<`, `>=`, `<=`.
- **Logické spojky:** `&&` (a zároveň - AND), `||` (nebo - OR), `!` (negace - NOT).
- **Bloky kódu:** Pokud je v podmínce více než jeden příkaz, musí být ve složených závorkách `{ }`.
- **Příkaz `break`:** U `switch` je kriticky důležitý pro ukončení větve. Bez něj by program "propadl" do dalších možností.
- **Default:** "Záchranná" větev ve `switch`, pokud nevyhovuje žádný `case`.