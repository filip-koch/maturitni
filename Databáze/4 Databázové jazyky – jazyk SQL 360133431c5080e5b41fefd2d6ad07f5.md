# 4. Databázové jazyky – jazyk SQL

---

SQL (**Structured Query Language**) je standardizovaný jazyk určený pro komunikaci s relačními databázemi. Pomocí něj definujeme strukturu dat, manipulujeme s nimi a vyhledáváme je.

### 1. Rozdělení jazyka SQL podle činnosti (4a)

Jazyk SQL se dělí do několika základních skupin podle toho, co s databází provádějí:

- **DDL (Data Definition Language) – Jazyk pro definici dat:** Slouží k vytváření, úpravě nebo odstraňování **struktury** databáze (tabulky, indexy, pohledy).
- **DML (Data Manipulation Language) – Jazyk pro manipulaci s daty:** Slouží k práci se samotnými **záznamy** v tabulkách (vkládání, mazání, úpravy).
- **DQL (Data Query Language) – Dotazovací jazyk:** Slouží k **vyhledávání** a výběru dat z databáze (příkaz `SELECT`). *Poznámka: Často se v literatuře řadí pod DML, ale pro přehlednost u zkoušky je lepší jej uvést samostatně.*

### 2. Syntaxe a příklady (4b)

Při zkoušce stačí uvést základní kostru příkazů pro každou skupinu:

**Příklad DDL (vytvoření tabulky):**

```sql
- Vytvoří tabulku 'Studenti' se dvěma sloupci
CREATE TABLE Studenti (
id_student INT PRIMARY KEY,
jmeno VARCHAR(50)
);
```

**Příklad DML (vložení dat):**

```sql
- Vloží nový záznam do tabulky
INSERT INTO Studenti (id_student, jmeno) VALUES (1, 'Jan Novák');
```

**Příklad DQL (výběr dat):**

```sql
- Vybere jména všech studentů z tabulky
SELECT jmeno FROM Studenti;
```

### 3. Klíčová slova a datové typy (4c)

Klíčová slova jsou vyhrazené výrazy, které mají v SQL pevný význam.

**Nejpoužívanější klíčová slova:**

- `CREATE`, `ALTER`, `DROP` (pro strukturu).
- `INSERT`, `UPDATE`, `DELETE` (pro data).
- `SELECT`, `FROM`, `WHERE`, `ORDER BY` (pro dotazy).

**Základní datové typy v SQL:**Aby systém věděl, co do sloupce ukládáme, musíme mu určit typ:

- **INT / INTEGER:** Celá čísla (např. věk, ID).
- **VARCHAR(n):** Textový řetězec proměnné délky (např. jméno, adresa); *n* určuje max. délku.
- **DATE / DATETIME:** Datum nebo datum a čas.
- **DECIMAL / FLOAT:** Desetinná čísla (např. cena, váha).
- **BOOLEAN:** Logická hodnota (pravda/nepravda).

---

### 💡 **Tahák pro maturanta (klíčové body):**

- **SQL** je univerzální jazyk pro práci s relačními databázemi.
- **Dělení:**
    - **DDL** = Stavíme „krabici“ (tabulku) – `CREATE`.
    - **DML** = Dáváme věci do krabice (záznamy) – `INSERT`.
    - **DQL** = Koukáme, co je v krabici – `SELECT`.
- **Základní typy:** `INT` (číslo), `VARCHAR` (text), `DATE` (datum).
- Pamatuj, že příkazy v SQL by měly být ukončeny středníkem `;`.