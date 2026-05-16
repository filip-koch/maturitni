# 16. Základy objektově orientovaného programování, třídy a objekty (Java)

---

### 1. Strukturované vs. Objektové programování

- **Strukturované programování (např. C):**
    - Program se skládá z dat a funkcí, které s nimi pracují.
    - Hlavní důraz je kladen na **algoritmus** (postup: "Co se má stát?").
    - Data a funkce jsou oddělené, což může vést k nepřehlednosti u velkých projektů.
- **Objektově orientované programování (Java):**
    - Program je vnímán jako soubor spolupracujících **objektů**.
    - Objekty v sobě spojují jak **data** (vlastnosti), tak **funkce** (schopnosti/metody).
    - Důraz je kladen na **data** a jejich interakci ("Kdo to dělá?").

### 2. Třída a Objekt

- **Třída (Class):**
    - Je to obecný **vzor, šablona nebo výkres**, podle kterého se objekty vytvářejí.
    - Definuje, jaké vlastnosti (proměnné) a schopnosti (metody) budou mít všechny objekty tohoto typu.
    - Sama o sobě v paměti nezabírá místo pro data (je to jen předpis).
- **Objekt (Instance):**
    - Je to konkrétní **jednotka** vytvořená podle třídy.
    - Zabírá místo v paměti a má své konkrétní hodnoty (např. třída je *Auto*, objekt je *moje červená Škoda*).

### 3. Tři pilíře OOP

1. **Zapouzdření (Encapsulation):**
    - Data (atributy) objektu jsou skryta před vnějším světem.
    - Přístup k nim je možný pouze přes veřejné metody (tzv. **gettery a settery**).
    - Výhoda: Bezpečnost a kontrola nad tím, co se s daty děje.
2. **Dědičnost (Inheritance):**
    - Umožňuje vytvářet nové třídy na základě již existujících.
    - Potomek přebírá (dědí) vlastnosti a metody předka a může přidat vlastní.
    - Výhoda: Znovupoužitelnost kódu (nemusíme psát to samé znovu).
3. **Polymorfismus (Mnohotvárnost):**
    - Schopnost různých objektů reagovat na stejné volání metody různým způsobem.
    - Příklad: Máme metodu `vydazvuk()`. U objektu *Pes* zaštěká, u objektu *Kocka* zamňouká.

### 4. Ukázka třídy v Javě

Při zkoušce je dobré načrtnout jednoduchou třídu:

Java

```java
// Definice třídy
public class Pes {
    // Atributy (vlastnosti) - zapouzdřené (private)
    private String jmeno;
    private int vek;

    // Konstruktor - metoda pro vytvoření objektu
    public Pes(String jmeno, int vek) {
        this.jmeno = jmeno;
        this.vek = vek;
    }

    // Metoda (schopnost)
    public void stekej() {
        System.out.println(jmeno + " říká: Haf!");
    }
}

// Použití v programu
Pes mujPes = new Pes("Alík", 3); // Vytvoření objektu (instance)
mujPes.stekej();
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **OOP** = data + funkce v jednom balíčku (objektu).
- **Třída** = výkres. **Objekt** = dům postavený podle výkresu.
- **Konstruktor** = speciální metoda, která se zavolá při vzniku objektu (klíčové slovo `new`).
- **Zapouzdření** = `private` atributy + `public` metody.
- **Dědičnost** = klíčové slovo `extends`.
- **Polymorfismus** = jedna zpráva, mnoho reakcí.