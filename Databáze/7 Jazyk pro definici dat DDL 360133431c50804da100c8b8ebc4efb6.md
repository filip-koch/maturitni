# 7. Jazyk pro definici dat DDL

---

### 1. Charakteristika DDL

Jazyk pro definici dat (Data Definition Language) je podmnožina SQL, která slouží k definování, změně a odstraňování **struktury** databázových objektů. Pomocí DDL nepracujeme s konkrétními řádky dat (záznamy), ale se samotným schématem databáze (tabulkami, sloupci, indexy).

### 2. Tvorba databáze a tabulek (7a)

Než začneme ukládat data, musíme vytvořit prostor a definovat pravidla.

- **Vytvoření databáze:** Slouží k založení nového kontejneru pro tabulky.
    - **Syntaxe:** `CREATE DATABASE nazev_databaze;`
- **Vytvoření tabulky:** Nejdůležitější DDL příkaz. Musíme definovat název tabulky, názvy sloupců, jejich datové typy a integritní omezení (klíče).
    - **Syntaxe:**
        
        ```sql
        CREATE TABLE Zamestnanci (
            id_zamestnance INT PRIMARY KEY, -- Primární klíč 
            jmeno VARCHAR(30) NOT NULL,    -- Povinné pole
            prijmeni VARCHAR(30) NOT NULL,
            datum_narozeni DATE
        );
        ```
        

### 3. Změny struktury tabulek (7b)

Pokud zjistíme, že v tabulce něco chybí nebo přebývá, použijeme příkaz **ALTER**. Ten umožňuje měnit strukturu bez nutnosti tabulku mazat a znovu vytvářet.

- **Přidání sloupce:** `ALTER TABLE Zamestnanci ADD email VARCHAR(50);`
- **Změna datového typu:** `ALTER TABLE Zamestnanci MODIFY email VARCHAR(100);`
- **Odstranění sloupce:** `ALTER TABLE Zamestnanci DROP COLUMN datum_narozeni;`

### 4. Odstraňování objektů (7b)

Když už tabulku nebo celou databázi nepotřebujeme, použijeme příkaz **DROP**.

- **DROP TABLE:** Nenávratně smaže celou tabulku i se všemi daty.
    - `DROP TABLE Zamestnanci;`
- **DROP DATABASE:** Smaže celou databázi včetně všech jejích tabulek.
    - `DROP DATABASE skola;`
- **TRUNCATE TABLE (bonus k maturitě):** Pokud chceš smazat všechna data v tabulce, ale zachovat její strukturu (prázdnou tabulku), použije se `TRUNCATE TABLE`. Je to rychlejší než mazání řádek po řádku.

---

### Základní integritní omezení v DDL

Při definici tabulek v rámci DDL často uvádíme omezení, která hlídají správnost dat:

- **PRIMARY KEY:** Unikátní identifikátor záznamu.
- **FOREIGN KEY:** Odkaz na jinou tabulku (zajišťuje vazby).
- **NOT NULL:** Pole nesmí zůstat prázdné.
- **UNIQUE:** Hodnota se nesmí v daném sloupci opakovat (např. e-mail).
- **DEFAULT:** Nastaví výchozí hodnotu, pokud uživatel žádnou nezadá.

---

### 💡 **Tahák pro maturanta (klíčové body):**

- **DDL = Definice struktury** (pracujeme s "krabicemi", ne s obsahem).
- **CREATE:** Vytváří (DATABASE, TABLE).
- **ALTER:** Mění (přidává/maže sloupce).
- **DROP:** Nadobro odstraňuje celou strukturu.
- V DDL příkazech definujeme **datové typy** (INT, VARCHAR, DATE) a **integritní omezení** (PRIMARY KEY).