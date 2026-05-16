# 11. Zpracování dat v My SQL, správa uživatelů

---

### 1. Import dat do databáze (11a)

Import slouží k naplnění databáze daty z vnějších zdrojů bez nutnosti je ručně vkládat přes `INSERT`.

- **Importovaný soubor** může mít různé formáty, nejčastěji se však setkáte s typem **.sql** nebo **.csv**.
- **SQL soubor (Dump):** Obsahuje kompletní SQL příkazy pro vytvoření struktury (`CREATE`) a vložení dat (`INSERT`).
- **CSV soubor:** Čistě textový soubor, kde jsou hodnoty odděleny čárkou nebo středníkem; používá se pro přenos tabulkových dat (např. z Excelu).
- V prostředí Workbench se k importu používá funkce **Data Import/Restore** v sekci Administration.

### 2. Generování modelu z databáze (11b)

Tento proces se nazývá **Reverse Engineering**. Umožňuje nám vytvořit vizuální schéma (diagram) z již existující databáze na serveru.

- **Značky pro kreslení:** Workbench používá notaci „vraní nožka“ (Crow's Foot) pro zobrazení vztahů mezi tabulkami.
- **Kardinalita vztahů:** Diagram jasně ukazuje, zda jde o vztah 1:1, 1:N nebo M:N.
- **Integritní omezení:** V modelu jsou vidět primární klíče (PK), cizí klíče (FK) a další pravidla (např. NOT NULL), která hlídají správnost dat.

### 3. Správa uživatelů a oprávnění (11c)

Bezpečnost databáze stojí na tom, že každý uživatel má přidělena pouze ta práva, která nezbytně potřebuje pro svou práci.

**Vytvoření nového uživatele:**
Provádí se příkazem `CREATE USER`. Musíme definovat jméno, hostitele (odkud se připojuje) a heslo.

```sql
- Vytvoření uživatele 'student' s přístupem z lokálního PC
CREATE USER 'student'@'localhost' IDENTIFIED BY 'heslo123';
```

**Přidělení oprávnění:**
K přidělení práv slouží příkaz `GRANT`. Můžeme povolit jen určité akce (např. jen čtení) na konkrétních tabulkách.

SQL

```sql
- Přidělení práva jen na čtení (SELECT) v databázi 'skola'
GRANT SELECT ON skola. TO 'student'@'localhost';

- Přidělení všech práv (vhodné pro správce)
GRANT ALL PRIVILEGES ON skola. TO 'admin'@'localhost';
```

**Odebrání oprávnění:** Pokud chceme práva vzít zpět, použijeme příkaz `REVOKE`.

SQL

```sql
REVOKE INSERT, UPDATE ON skola.* FROM 'student'@'localhost';
```

---

### 💡 **Tahák pro maturanta (klíčové body):**

- **Import:** Nejčastěji soubory **.sql** (skripty) nebo **.csv** (tabulková data).
- **Reverse Engineering:** Proces vytvoření grafického modelu z hotové databáze.
- **Model:** Zobrazuje tabulky, jejich vazby (kardinalitu) a omezení (klíče).
- **Uživatelé:** Vytváříme pomocí `CREATE USER`.
- **Práva:** Přidělujeme pomocí `GRANT` a odebíráme přes `REVOKE`.
- **Princip minimálních privilegií:** Uživatel má mít jen ta práva, která nutně potřebuje.