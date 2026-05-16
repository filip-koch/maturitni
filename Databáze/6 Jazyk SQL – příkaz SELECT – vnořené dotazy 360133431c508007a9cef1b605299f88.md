# 6. Jazyk SQL – příkaz SELECT – vnořené dotazy

---

### 1. Typy spojení tabulek (6a)

Spojování tabulek (JOIN) je základní operací v relačních databázích, která umožňuje kombinovat záznamy ze dvou a více tabulek na základě společného sloupce (typicky primární a cizí klíč).

- **INNER JOIN:** Vrátí pouze ty záznamy, které mají shodu v obou tabulkách. Pokud záznam v jedné tabulce nemá odpovídající protějšek ve druhé, ve výsledku nebude.
- **LEFT JOIN (vnější):** Vrátí všechny záznamy z levé tabulky a k nim odpovídající záznamy z pravé tabulky. Pokud shoda neexistuje, doplní se hodnoty `NULL`.
- **RIGHT JOIN (vnější):** Funguje opačně než LEFT JOIN; vrátí všechny záznamy z pravé tabulky a k nim odpovídající z levé.
- **CROSS JOIN:** Vytvoří kartézský součin – každý řádek první tabulky spojí s každým řádkem druhé tabulky.

### 2. Vnořené dotazy vracející jednu hodnotu (6b)

Vnořený dotaz (subquery) je příkaz `SELECT` umístěný uvnitř jiného SQL příkazu (např. v sekci `WHERE`). Skalární vnořený dotaz vrací **právě jednu hodnotu** (jeden řádek a jeden sloupec).

- **Využití:** Často se používá k porovnání s výsledkem agregační funkce.
- **Příklad:** Najdi studenty, kteří mají lepší průměr než je celkový průměr školy.
    
    ```sql
    SELECT jmeno FROM Studenti 
    WHERE prumer < (SELECT AVG(prumer) FROM Studenti);
    ```
    

### 3. Vnořené dotazy vracející více hodnot a operátory (6c)

Pokud vnořený dotaz vrací seznam hodnot (jeden sloupec, více řádků), musíme použít speciální operátory:

- **IN:** Vrátí `TRUE`, pokud se hledaná hodnota nachází v seznamu výsledků vnořeného dotazu.
- **ANY / SOME:** Vrátí `TRUE`, pokud hledaná hodnota splňuje podmínku alespoň pro **jeden** prvek z výsledku vnořeného dotazu.
- **ALL:** Vrátí `TRUE`, pouze pokud hledaná hodnota splňuje podmínku pro **všechny** prvky z výsledku.
- **EXISTS:** Nekontroluje konkrétní hodnotu, ale pouze to, zda vnořený dotaz vrátil **alespoň jeden řádek**. Je velmi efektivní pro kontrolu existence vazeb.

---

### Praktický příklad použití operátoru IN:

SQL

```sql
- Vybere studenty, kteří jsou zapsáni v konkrétních kroužcích
SELECT jmeno FROM Studenti
WHERE id_student IN (SELECT id_student FROM Krouzky WHERE nazev = 'IT');
```

---

### 💡 **Tahák pro maturanta (klíčové body):**

- **INNER JOIN** = jen shoda; **LEFT/RIGHT JOIN** = vše z jedné strany + shoda z druhé.
- **Vnořený dotaz** je dotaz v dotazu; musí být v kulatých závorkách `()`.
- Pokud vrací **jednu hodnotu**, použij klasické operátory (`=`, `<`, `>`).
- Pokud vrací **seznam**, použij `IN`, `ANY` nebo `ALL`.
- **EXISTS** se ptá: „Existuje v té druhé tabulce k tomuto řádku aspoň jeden záznam?“.