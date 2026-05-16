# 5. Jazyk SQL – příkaz SELECT

---

### 1. Struktura příkazu SELECT (5a)

Příkaz SELECT se skládá z povinných a nepovinných částí. Je důležité dodržet jejich přesné pořadí:

- **SELECT** (povinné): Určuje, které sloupce chceme vypsat.
- **FROM** (povinné): Určuje tabulku, ze které data čerpáme.
- **WHERE** (nepovinné): Podmínka pro filtrování řádků (např. `cena > 100`).
- **GROUP BY** (nepovinné): Seskupování záznamů podle určitého kritéria.
- **HAVING** (nepovinné): Podmínka pro již vytvořené skupiny (používá se s agregacemi).
- **ORDER BY** (nepovinné): Řazení výsledků (vzestupně `ASC`, sestupně `DESC`).

### 2. Práce se sloupci a omezení duplicit (5b)

V části SELECT můžeme s daty dále manipulovat:

- **Výběr všech sloupců:** Používá se hvězdička (`SELECT *`).
- **Přejmenování (Aliasy):** Pomocí klíčového slova `AS` můžeme sloupec pro výstup přejmenovat (např. `SELECT jmeno AS Jmeno_Studenta`).
- **Výpočty:** Přímo v SELECTu lze provádět matematické operace (např. `SELECT cena * 1.21 AS cena_s_dph`).
- **Omezení duplicit:** Klíčové slovo `DISTINCT` zajistí, že se každý výsledek vypíše pouze jednou, i kdyby byl v tabulce vícekrát.

### 3. Seskupování a agregační funkce (5c)

Seskupování (`GROUP BY`) používáme, když nechceme vidět jednotlivé záznamy, ale souhrnné informace za určité skupiny (např. průměrný plat podle oddělení).

**Nejdůležitější agregační funkce:**

- `COUNT()`: Spočítá počet záznamů.
- `SUM()`: Sečte hodnoty v daném sloupci.
- `AVG()`: Vypočítá průměrnou hodnotu.
- `MIN()` / `MAX()`: Najde nejnižší nebo nejvyšší hodnotu.

### 4. Pohledy (Views) (5d, 5e)

**Pohled** je „virtuální tabulka“. Neobsahuje vlastní data, je to pouze uložený dotaz SELECT pod určitým názvem.

**Význam pohledů:**

- **Zjednodušení:** Místo psaní složitého dotazu s mnoha spoji (JOIN) pokaždé znovu, stačí zavolat pohled.
- **Bezpečnost:** Uživateli můžeme povolit přístup k pohledu, který obsahuje jen některé sloupce, místo přístupu k celé zdrojové tabulce.

**Příklady práce s pohledy:**

SQL

```sql
- Vytvoření pohledu
CREATE VIEW SeznamStudentu AS
SELECT jmeno, prijmeni FROM Studenti;

- Úprava pohledu (pokud systém podporuje OR REPLACE)
CREATE OR REPLACE VIEW SeznamStudentu AS
SELECT jmeno, prijmeni, email FROM Studenti;
```

---

### 💡 **Tahák pro maturanta (klíčové body):**

- **SELECT a FROM** jsou povinné.
- **DISTINCT** odstraňuje duplicity z výsledku.
- **WHERE** filtruje řádky, **HAVING** filtruje skupiny.
- **Agregace** (`SUM`, `AVG`, `COUNT`...) vyžadují pro správný výsledek často `GROUP BY`.
- **VIEW** je jen uložený dotaz, který se chová jako tabulka, ale data fyzicky nedrží.