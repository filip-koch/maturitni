# 9. Databázový systém My SQL – prostředí Workbench

---

### **1. Charakteristika MySQL Workbench**

MySQL Workbench je komplexní grafické uživatelské rozhraní (GUI) pro databázový systém MySQL. Slouží vývojářům a administrátorům k vizuálnímu návrhu, správě a údržbě databází. Místo psaní všech příkazů ručně do příkazového řádku umožňuje provádět většinu operací pomocí klikání a formulářů.  

### **2. Pracovní prostředí Workbench (9a)**

Při popisu prostředí se zaměř na tyto základní oblasti, které uvidíš po spuštění a připojení k serveru:

- **Navigator (Levý panel):** Obsahuje dvě hlavní karty – **Administration** (správa serveru, uživatelů, export/import) a **Schemas** (seznam tvých databází a jejich objektů).
- **SQL Editor (Centrální část):** Hlavní okno, kam píšeš SQL dotazy. Horní lišta obsahuje ikonu „blesku“ pro spuštění kódu.
- **Results Grid (Dolní část):** Zde se zobrazují výsledky tvých dotazů (data z tabulek).
- **Output Area:** Záznam o provedených operacích – zde zjistíš, zda příkaz proběhl v pořádku, nebo kde nastala chyba (červená ikona).

### **3. Databázové objekty a práce s nimi (9b)**

V prostředí Workbench pracujeme s objekty, které jsou hierarchicky uspořádány:

- **Schémata (Databáze):** Nejvyšší úroveň kontejneru.
- **Tabulky (Tables):** Základní stavební kameny pro data. Workbench umožňuje přes pravé tlačítko myši zvolit **"Alter Table"**, kde lze v grafickém editoru měnit sloupce, datové typy a klíče.
- **Indexy:** Slouží k urychlení vyhledávání v tabulkách.
- **Cizí klíče (Foreign Keys):** Workbench má pro ně v editoru tabulek samostatnou kartu, kde se vizuálně definují vazby mezi tabulkami.

### **4. Úloha pohledů v databázových systémech (9c)**

Pohledy (**Views**) jsou v MySQL Workbench velmi důležité pro usnadnění práce:  

- **Definice:** Pohled je „virtuální tabulka“ vytvořená na základě SQL dotazu.
- **Bezpečnost:** Můžeme uživateli zpřístupnit pohled, který neobsahuje citlivé údaje (např. skryje platy zaměstnanců), místo celé tabulky.
- **Zjednodušení:** Pokud často spojujeme pět tabulek pomocí složitých JOINů, uložíme si tento dotaz jako pohled a příště se na něj dotazujeme jednoduše jako na běžnou tabulku.

### **Praktická ukázka v prostředí**

Pro vytvoření nového objektu (např. tabulky) stačí v Navigátoru kliknout pravým tlačítkem na složku **Tables** a vybrat **Create Table**. Workbench ti otevře formulář, kde vyplníš názvy polí a zaškrtneš vlastnosti jako:
• **PK** (Primary Key) – Primární klíč.
• **NN** (Not Null) – Pole nesmí být prázdné.
• **AI** (Auto Increment) – Automatické číslování (vhodné pro ID).

### 💡 **Tahák pro maturanta (klíčové body):**

- **Workbench** = Grafické „vylepšení“ pro práci s MySQL.
- **Navigátor:** Přepínání mezi správou (Administration) a databázemi (Schemas).
- **SQL Editor:** Místo pro psaní a spouštění dotazů.
- **Objekty:** Tabulky, pohledy, indexy, cizí klíče.
- **Pohledy (Views):** Virtuální tabulky pro zjednodušení a bezpečnost