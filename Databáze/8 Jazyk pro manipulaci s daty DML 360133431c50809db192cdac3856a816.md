# 8. Jazyk pro manipulaci s daty DML

---

### 1. Charakteristika DML

Jazyk pro manipulaci s daty (Data Manipulation Language) slouží k práci se samotnými daty, která jsou již v databázi uložena. Mezi základní operace patří přidávání, úprava a odstraňování záznamů.

### 2. Základní operace a jejich syntaxe (8a)

U maturity bys měl být schopen vysvětlit tyto tři základní příkazy:

- **INSERT INTO (Přidávání dat):** Slouží k vložení nového řádku (záznamu) do tabulky.
    - **Příklad:** `INSERT INTO Studenti (id, jmeno) VALUES (1, 'Petr');`
- **UPDATE (Změna dat):** Slouží k úpravě stávajících hodnot v tabulce.
    - **Klíčové upozornění:** Vždy je nutné použít klauzuli `WHERE`, jinak se změní data ve všech řádcích tabulky!
    - **Příklad:** `UPDATE Studenti SET jmeno = 'Pavel' WHERE id = 1;`
- **DELETE (Odstranění dat):** Slouží ke smazání konkrétních záznamů.
    - **Klíčové upozornění:** I zde je klauzule `WHERE` kritická, jinak dojde ke smazání všech dat v tabulce (ale tabulka samotná zůstane prázdná).
    - **Příklad:** `DELETE FROM Studenti WHERE id = 1;`

### 3. Typy dotazů (tzv. Akční dotazy) (8b)

V kontextu databázových systémů (často se takto označují v MS Access) dělíme dotazy, které mění data, na několik typů:

- **Aktualizační dotazy (Update):** Změní hodnoty v existujících polích na základě určité podmínky.
- **Vytvářecí dotazy (Make-Table):** Na základě výsledku výběru vytvoří zcela novou tabulku a do ní data uloží.
- **Přidávací dotazy (Append):** Vezmou vybraná data z jedné tabulky a připojením je vloží na konec jiné existující tabulky.
- **Odstraňovací dotazy (Delete):** Smažou celou skupinu záznamů, které odpovídají zadaným kritériím.

### 4. Bezpečnost a integrita při manipulaci

Při používání DML příkazů je důležité zmínit, že systém hlídá **integritní omezení**. Například:

- Nemůžeš smazat záznam, na který odkazuje jiná tabulka (pokud není nastaveno kaskádové mazání).
- Nemůžeš vložit do primárního klíče hodnotu, která už existuje.
- Nemůžeš nechat prázdné pole, které má nastaveno `NOT NULL`.

---

### 💡 **Tahák pro maturanta (klíčové body):**

- **DML = Práce se záznamy** (řádky v tabulce).
- **INSERT:** Vloží nový řádek.
- **UPDATE:** Změní existující data (nezapomeň na `WHERE`!).
- **DELETE:** Smaže řádky (nezapomeň na `WHERE`!).
- **Akční dotazy:** Aktualizační, vytvářecí, přidávací a odstraňovací.
- DML příkazy musí respektovat **integritní omezení** (klíče, NOT NULL).