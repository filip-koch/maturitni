# 13. Výběrové dotazy, dotaz s parametrem a křížový dotaz v MS Access

---

### 1. Návrhové zobrazení dotazu (13a)

V MS Access se dotazy nejčastěji tvoří v grafickém prostředí zvaném **Návrhové zobrazení**. Toto okno je rozděleno na dvě části:

- **Horní část:** Zde vybíráme tabulky (nebo jiné dotazy), se kterými chceme pracovat.
- **Dolní část (mřížka QBE – Query By Example):** Zde definujeme:
    - **Pole:** Které sloupce chceme zobrazit.
    - **Tabulka:** Ze které tabulky pole pochází.
    - **Řazení:** Zda má být výsledek vzestupný nebo sestupný.
    - **Zobrazit:** Zaškrtávací políčko, zda má být sloupec ve výsledku vidět.
    - **Kritéria:** Podmínky pro filtrování (např. `>500` nebo `"Praha"`).

### 2. Spojování tabulek v dotazu (13b)

Aby dotaz mohl čerpat data z více tabulek najednou, musí mezi nimi existovat **relace** (spojnice).

- V dotazu se spojení obvykle vytvoří automaticky, pokud jsou relace již definovány v databázi.
- Můžeme upravit typ spojení (Join):
    - **Vnitřní spojení:** Zobrazí jen záznamy, které mají shodu v obou tabulkách.
    - **Vnější spojení:** Zobrazí všechny záznamy z jedné tabulky a k nim odpovídající z druhé (i ty, které protějšek nemají).

### 3. Agregace a výpočty (13c)

- **Agregační funkce:** Pokud v návrhu zapneme řádek **Souhrny (Totals)**, můžeme provádět výpočty nad skupinami dat. Mezi základní patří `Suma` (součet), `Průměr` (AVG), `Počet` (COUNT), `Min` a `Max`.
- **Tvůrce výrazů:** Nástroj, který nám pomáhá psát vzorce pro výpočtová pole (např. vytvoření sloupce „Cena s DPH“ jako `[Cena] * 1.21`).

### 4. Dotaz s parametrem a křížový dotaz

- **Dotaz s parametrem:** Místo pevné podmínky (např. "Praha") napíšeme do kritérií text v hranatých závorkách: `[Zadejte město]`. Při spuštění se Access uživatele zeptá na hodnotu.
- **Křížový dotaz:** Slouží k přehlednému shrnutí dat do formátu podobného kontingenční tabulce (řádky, sloupce a v průsečíku vypočítaná hodnota, např. součet prodejů podle měsíců a kategorií zboží).

### 5. Výkonné (akční) dotazy (13d, 13e, 13f)

Na rozdíl od výběrových dotazů, které data jen zobrazují, **výkonné dotazy** provádějí s daty změny.

- **Rozdíl:** Výběrový dotaz nemění původní tabulky, výkonný ano.
- Typy výkonných dotazů:
    1. **Aktualizační:** Hromadně mění hodnoty v existujících polích (např. „zdraž vše o 10 %“).
    2. **Vytvářecí:** Na základě výsledku dotazu vytvoří zcela novou tabulku.
    3. **Přidávací:** Vloží výsledky dotazu na konec jiné existující tabulky.
    4. **Odstraňovací:** Smaže záznamy, které splňují podmínku.

---

### 💡 **Tahák pro maturanta (klíčové body):**

- **Návrhové zobrazení** je mřížka, kde skládáme dotaz (Pole, Kritéria, Řazení).
- **Souhrny** zapínají agregační funkce (Suma, Počet...).
- **Výběrový dotaz** jen „ukazuje“, **Výkonný dotaz** „koná“ (mění, maže, přidává).
- **Parametr** se píše do `[hranatých závorek]` a umožňuje interaktivní filtrování.
- **Relace** v dotazu jsou nutné pro čerpání dat z více zdrojů.