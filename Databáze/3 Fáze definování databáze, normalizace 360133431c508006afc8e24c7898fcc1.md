# 3. Fáze definování databáze, normalizace

---

### 1. Definování a fáze návrhu (3a, 3b, 3c)

Definování (nebo návrh) databáze je proces transformace požadavků z reálného světa do struktury, kterou dokáže zpracovat počítač. Celý proces se dělí do čtyř logických fází:

- **Analýza požadavků:** Zjišťujeme, k čemu bude databáze sloužit, jaká data budeme ukládat a kdo k nim bude mít přístup.
- **Konceptuální návrh:** Vytvoření abstraktního modelu (nejčastěji E-R diagram), který popisuje objekty a vztahy mezi nimi bez ohledu na konkrétní software.
- **Logický návrh:** Převod E-R diagramu do struktury tabulek, definování primárních a cizích klíčů a provedení normalizace.
- **Fyzický návrh:** Konkrétní implementace v určitém systému (např. MySQL), nastavení datových typů, indexů a úložiště na disku.

### 2. Základní prvky a modely (3d, 3e)

Při návrhu pracujeme se třemi základními prvky:

- **Entita:** Předmět nebo osoba z reality (např. **Student**, **Zboží**).
- **Atribut:** Vlastnost dané entity (např. **Jméno** studenta, **Cena** zboží).
- **Vztah:** Logické spojení mezi entitami (např. Student **navštěvuje** Předmět).

**Rozdíl v úrovních modelování:**

- **Konceptuální:** Jen „obrázek“ entit a vztahů (E-R diagram).
- **Logický:** Tabulky se sloupci a vazbami (relační model), ale bez technických detailů.
- **Fyzický:** Skutečný kód v SQL nebo soubor v MS Access.

### 3. Redundance a normalizace (3f, 3g)

**Redundance** je stav, kdy jsou stejná data v databázi uložena na více místech zbytečně. To vede k plýtvání místem a riziku chyb (při opravě zapomeneme data přepsat na všech místech).
**Normalizace** je proces optimalizace tabulek s cílem tuto redundanci odstranit a zajistit datovou integritu.

### 4. Normální formy (3h, 3i)

U maturity stačí charakterizovat první tři formy:

- **1. normální forma (1NF):** Všechna pole musí obsahovat atomické (nedělitelné) hodnoty. Žádné pole nesmí obsahovat seznam hodnot nebo více údajů (např. v poli „Telefon“ nesmí být dvě čísla najednou).
- **2. normální forma (2NF):** Musí splňovat 1NF a všechny neklíčové atributy musí být plně závislé na celém primárním klíči. To se řeší hlavně u tabulek se složeným klíčem – pokud něco závisí jen na části klíče, musí to do nové tabulky.
- **3. normální forma (3NF):** Musí splňovat 2NF a mezi neklíčovými atributy nesmí existovat tranzitivní závislost. To znamená, že neklíčový sloupec nesmí záviset na jiném neklíčovém sloupci (např. „Město“ závisí na „PSČ“, nikoliv přímo na ID studenta).

---

### 💡 **Tahák pro maturanta (klíčové body):**

- **Fáze:** Analýza -> Konceptuální (diagram) -> Logický (tabulky) -> Fyzický (SQL/Access).
- **Objekty:** Entita (co), Atribut (vlastnost), Vztah (vazba).
- **Normalizace:** Čištění databáze od zbytečností (redundance).
- **1NF:** Pole jsou nedělitelná (atomická).
- **2NF:** Odstranění závislostí na části složeného klíče.
- **3NF:** Odstranění závislostí mezi běžnými sloupci navzájem.