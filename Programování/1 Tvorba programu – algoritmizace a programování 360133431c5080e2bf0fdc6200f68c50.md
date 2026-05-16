# 1. Tvorba programu – algoritmizace a programování

---

### 1. Postup při řešení problému (etapy)

Při tvorbě programu nezačínáme psaním kódu, ale procházíme několika fázemi:

**Formulace problému:** Přesné určení zadání, co jsou vstupní data a jaké mají být výsledky.

1. **Analýza úlohy:** Zjištění, zda je úloha řešitelná a jaké matematické či logické vztahy použijeme.
2. **Vytvoření algoritmu:** Sestavení jednoznačného postupu krok za krokem.
3. **Sestavení vývojového diagramu:** Grafické znázornění postupu pro lepší přehlednost.
4. **Sestavení programu:** Přepis algoritmu do konkrétního jazyka (např. C nebo Java).
5. **Odladění (Debugging):** Hledání a oprava chyb, ověření správnosti na testovacích datech.

### 2. Definice a vlastnosti algoritmu

**Definice:** Algoritmus je přesný návod či postup, kterým ze zadaných vstupních údajů získáme po konečném počtu kroků správný výsledek.

Aby byl postup považován za algoritmus, musí splňovat tyto vlastnosti:

- **Elementárnost:** Skládá se z jednoduchých, srozumitelných kroků.
- **Determinovanost:** V každém okamžiku je jasné, jaký krok následuje.
- **Konečnost:** Musí skončit v reálném čase (nesmí se zacyklit navždy).
- **Rezultativnost:** Pro stejné vstupy dává vždy stejné výsledky.
- **Hromadnost (Univerzálnost):** Řeší celou třídu podobných úloh (např. výpočet obsahu jakéhokoliv čtverce, ne jen toho se stranou 5).
- **Efektivnost:** Dosáhne výsledku v co nejkratším čase a s minimem prostředků.

### 3. Možnosti zápisu algoritmu

Algoritmus můžeme zapsat několika způsoby:

1. **Slovní vyjádření:** Podobné receptu v kuchařce (vhodné pro laiky).
2. **Matematické vyjádření:** Pomocí vzorců a rovnic.
3. **Grafické vyjádření (Vývojové diagramy):** Nejpřehlednější forma využívající značky jako ovál (start/konec), obdélník (činnost) nebo kosočtverec (rozhodování) .
4. **Počítačový program:** Algoritmus zapsaný v programovacím jazyce.

### 4. Zpracování programu v jazyce C

Program v jazyce C prochází cestou od textového souboru k spustitelné aplikaci:

1. **Editor:** Zde programátor píše zdrojový kód (soubor `.c`).
2. **Preprocesor:** Zpracuje direktivy začínající `#` (např. `#include` pro vložení knihoven).
3. **Compiler (Překladač):** Přeloží zdrojový kód do relativního (strojového) kódu (soubor `.obj`).
4. **Linker (Spojovač):** Propojí objektové soubory a knihovny do jednoho spustitelného souboru (soubor `.exe`).
5. **Debugger:** Nástroj pro hledání chyb a „krokování“ programu.

---

### Praktický příklad: Záměna dvou proměnných (Swap)

Tento algoritmus se často u zkoušky kreslí na tabuli. Potřebujeme pomocnou nádobu (proměnnou `pom`).

**Kód v C:**

```c
#include <stdio.h>

int main() {
    int a = 3, b = 5;
    int pom; // Pomocná proměnná

    pom = a; // Krok 1: schovám si 'a' do 'pom'
    a = b;   // Krok 2: do 'a' dám hodnotu 'b'
    b = pom; // Krok 3: do 'b' dám schovanou hodnotu z 'pom'

    printf("a = %d, b = %d", a, b); // Vypíše: a = 5, b = 3
    return 0;
}
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Algoritmus** = přesný návod k řešení úlohy.
- **Vlastnosti:** pamatuj si trojici **Konečnost, Determinovanost, Hromadnost** .
- **Vývojový diagram** je mezinárodní „obrázkový“ jazyk programátorů.
- **Cesta kódu v C:** Zdroják (`.c`) → Preprocesor → Kompilátor (`.obj`) → Linker → Spustitelný soubor (`.exe`) .
- **Case Sensitivity:** Jazyk C rozlišuje velká a malá písmena (`Suma` není to samé co `suma`)