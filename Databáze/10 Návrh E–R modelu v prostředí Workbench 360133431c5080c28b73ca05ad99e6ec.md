# 10. Návrh E–R modelu v prostředí Workbench

---

## 10. Návrh E-R modelu v prosředí Workbench

### 1. Pracovní prostředí Modeler (10a)

MySQL Workbench Modeler je vizuální nástroj, který neslouží k psaní kódu, ale k „kreslení“ architektury databáze.

**Klíčové části prostředí:**

- **Model tab (Karta modelu):** Obsahuje přehled všech tabulek, pohledů a schémat v daném modelu.
- **Diagram (Plátno):** Hlavní plocha, kam se přetahují tabulky a kde se tvoří vazby.
- **Vertical Toolbar (Svislý panel nástrojů):** Obsahuje nástroje pro tvorbu nové tabulky (ikona tabulky) a různé typy relací (čáry pro 1:1, 1:N, N:M).
- **Layer (Vrstvy):** Umožňují logicky seskupovat tabulky (např. barevně odlišit tabulky pro uživatele a tabulky pro zboží).

### 2. Návrh modelu – značky a kardinalita (10b)

V prostředí Workbench se nepoužívá klasická školní notace (oválky pro atributy), ale tzv. **Crow's Foot notation** (notace vraní nožky), která je přehlednější pro složité systémy.

- **Tabulky:** Jsou zobrazeny jako obdélníky rozdělené na části: Název tabulky, Primární klíč (horní část) a ostatní atributy (dolní část).
- **Atributy:** U každého sloupce definujeme datový typ a zkratky integritních omezení:
    - **PK (Primary Key):** Primární klíč.
    - **NN (Not Null):** Povinné pole.
    - **UQ (Unique):** Unikátní hodnota.
    - **AI (Auto Increment):** Automatické číslování.
- **Kardinalita:** Vztahy jsou znázorněny čarami:
    - **1:1:** Čára s jednou čárkou na obou koncích.
    - **1:N:** Čára, která se na jedné straně větví (jako „vraní nožka“).
    - **N:M:** Workbench při použití nástroje pro N:M vztah automaticky vytvoří **vazební tabulku**, což je v relačních databázích nutnost.

### 3. Úpravy modelu (10c)

Workbench je velmi flexibilní a umožňuje model kdykoliv změnit:

- **Změna struktury:** Dvojklikem na tabulku se otevře editor, kde lze přidávat sloupce nebo měnit datové typy.
- **Vizuální úpravy:** Tabulky lze libovolně přesouvat, měnit jejich barvy pro lepší orientaci nebo přidávat textové poznámky.
- **Vztahy:** Lze měnit typy vazeb (např. z identifikující na neidentifikující vazbu).

### 4. Propojení s realitou (Forward Engineering)

U maturity velmi zapůsobí, když zmíníš funkci **Forward Engineering**. Je to proces, kdy Workbench vezme tvůj nakreslený diagram a automaticky vygeneruje SQL kód (`CREATE TABLE`...), který následně spustí na serveru a vytvoří skutečnou databázi.

---

### 💡 **Tahák pro maturanta (klíčové body):**

- **Modeler** = Nástroj pro vizuální návrh bez nutnosti psát SQL.
- **Notace:** Používá se „vraní nožka“ pro znázornění vazeb.
- **Tabulka:** Obsahuje sloupce s definovanými vlastnostmi (PK, NN, AI).
- **Relace:** 1:1, 1:N a automatická tvorba vazební tabulky u N:M.
- **Změny:** Model lze kdykoliv editovat (barvy, sloupce, typy vazeb).
- **Forward Engineering:** Převod obrázku na skutečný SQL kód.