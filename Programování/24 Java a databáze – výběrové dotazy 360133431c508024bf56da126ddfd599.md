# 24. Java a databáze – výběrové dotazy

---

### 1. Nastavení a připojení k databázi

Pro práci s výběrovými dotazy platí stejné základy jako u DML:

- **Projekt:** V souboru `module-info.java` musí být uveden řádek `requires java.sql;`.
- **Connection:** Spojení navážeme pomocí `DriverManager.getConnection(url, username, password)`.
- **Knihovna:** Projekt musí obsahovat JDBC ovladač pro konkrétní databázi (např. MySQL Connector).

### 2. SQL SELECT v Javě

Výběrový dotaz `SELECT` slouží k získání dat z jedné nebo více tabulek.

- **Části dotazu:**
    - `SELECT`: definuje sloupce, které chceme získat.
    - `FROM`: určuje tabulku.
    - `WHERE`: filtruje data podle podmínek.
    - `ORDER BY`: určuje řazení výsledků.
- **Provedení:** V Javě používáme k provedení výběru metodu **`executeQuery()`** rozhraní `PreparedStatement`. Na rozdíl od `executeUpdate()` vrací tato metoda objekt typu **`ResultSet`**.

### 3. Rozhraní ResultSet

`ResultSet` si můžeme představit jako tabulku v paměti, která obsahuje výsledky dotazu. K datům přistupujeme pomocí tzv. **kurzoru**, který původně ukazuje před první řádek.

- **Procházení dat (`next()`):** Metoda `next()` posune kurzor na další řádek. Vrací `true`, pokud řádek existuje, a `false`, pokud jsme na konci. Proto se nejčastěji používá v cyklu `while`.
- **Získávání hodnot:** Podle datového typu sloupce voláme příslušné metody:
    - `getInt(název_sloupce)` nebo `getInt(index)`.
    - `getString(název_sloupce)`.
    - `getDouble()`, `getDate()` a další.

### 4. Práce s parametry

Stejně jako u zápisu, i u výběru je nutné používat **zástupné znaky `?`** pro ochranu před SQL Injection.

- **Příklad:** `SELECT * FROM uzivatele WHERE id = ?`
- Hodnotu za otazník dosadíme pomocí `ps.setInt(1, id_hledaneho)`.

---

### Praktický příklad: Výpis všech studentů z databáze

Java

```java
import java.sql.*;

public class VyberDat {
    public static void main(String[] args) {
        String url = "jdbc:mysql://localhost/skola";
        String sql = "SELECT jmeno, vek FROM studenti WHERE vek > ?";

        try (Connection conn = DriverManager.getConnection(url, "root", "");
             PreparedStatement ps = conn.prepareStatement(sql)) {
            
            // Nastavení parametru pro WHERE
            ps.setInt(1, 18);
            
            // Spuštění dotazu a získání výsledků
            ResultSet rs = ps.executeQuery();
            
            // Procházení výsledků řádek po řádku
            while (rs.next()) {
                String jmeno = rs.getString("jmeno"); // Přístup přes jméno sloupce
                int vek = rs.getInt("vek");
                System.out.println("Student: " + jmeno + ", věk: " + vek);
            }
            
            rs.close(); // Uzavření ResultSetu
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **`executeQuery()`** vrací objekt **`ResultSet`**, zatímco `executeUpdate()` vrací `int`.
- **`ResultSet`** je výsledková sada, kterou musíme projít cyklem `while(rs.next())`.
- **Metody `get`** (např. `getString`, `getInt`) slouží k vytažení konkrétních dat z aktuálního řádku.
- **SQL Injection:** Vždy používej `PreparedStatement` a otazníky, nikdy nevkládej proměnné přímo do řetězce SQL dotazu.
- **Zavírání:** Všechny prostředky (`Connection`, `PreparedStatement`, `ResultSet`) by měly být uzavřeny metodou `.close()`.