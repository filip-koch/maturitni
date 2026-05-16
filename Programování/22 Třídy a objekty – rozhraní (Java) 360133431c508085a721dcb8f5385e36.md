# 22. Třídy a objekty – rozhraní (Java)

---

### 1. Abstraktní třída

Abstraktní třída je třída, která slouží jako částečný vzor pro jiné třídy. Je to „nedokončený výkres“.

- **Vlastnosti:**
    - Nelze z ní vytvořit objekt (instanci) pomocí klíčového slova `new`.
    - Definuje se klíčovým slovem **`abstract`**.
    - Může obsahovat běžné metody s tělem i **abstraktní metody** (bez těla, končí středníkem).
    - Obsahuje atributy (proměnné) a konstruktory, které využívají její potomci.
- **Účel:** Slouží jako společný základ pro logicky příbuzné třídy (např. třída *Tvar* je abstraktní, ale *Kruh* a *Ctverec* jsou konkrétní).

---

### 2. Rozhraní (Interface) a jeho konstrukce

Rozhraní je čistý předpis chování. Je to „smlouva“, kterou se třída zavazuje splnit.

- **Konstrukce:**
    - Definuje se klíčovým slovem **`interface`**.
    - Standardně obsahuje pouze hlavičky metod (abstraktní metody) a konstanty.
    - Všechny metody v rozhraní jsou automaticky `public` a `abstract`.
    - Třída, která chce rozhraní používat, použije klíčové slovo **`implements`**.
- **Vícenásobná implementace:** V Javě může třída implementovat **více rozhraní najednou**, což řeší problém chybějící vícenásobné dědičnosti.

---

### 3. Využití rozhraní a abstraktní třídy

Rozhraní a abstraktní třídy se využívají k dosažení vysoké míry flexibility a polymorfismu.

- **Příklady z praxe (Java API):**
    - **`ResultSet`**: Rozhraní pro práci s výsledky databázových dotazů.
    - **`ObservableList`**: Rozhraní používané v JavaFX pro seznamy, které umí upozornit na své změny.
- **Kdy co použít?**
    - **Abstraktní třída:** Když máme objekty, které mají společný základ a sdílejí i nějaký kód (vztah „je-a“).
    - **Rozhraní:** Když chceme definovat společnou schopnost pro různé objekty, které jinak spolu nesouvisí (vztah „umí-to“). Např. rozhraní *Létající* může implementovat *Pták* i *Letadlo*.

---

### Praktický příklad: Rozhraní vs. Abstraktní třída

Java

```java
// Abstraktní třída - společný základ
abstract class HudebniNastroj {
    String nazev;
    // Abstraktní metoda - každý nástroj hraje jinak
    public abstract void hraj();
}

// Rozhraní - doplňková schopnost
interface Laditelny {
    void naladit(); // Metoda bez těla
}

// Konkrétní třída implementuje i dědí
class Kytara extends HudebniNastroj implements Laditelny {
    @Override
    public void hraj() {
        System.out.println("Brnkám na struny.");
    }

    @Override
    public void naladit() {
        System.out.println("Napínám struny kolíkem.");
    }
}
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Abstraktní třída (`abstract`)** = částečná implementace, základ pro příbuzné třídy. Nelze z ní tvořit objekty.
- **Rozhraní (`interface`)** = čistá smlouva o chování. Neobsahuje těla metod (do Javy 8).
- **`extends`** vs. **`implements`** = dědíme z jedné třídy, ale implementovat můžeme libovolný počet rozhraní.
- **Polymorfismus** = proměnná může být typu rozhraní (např. `ResultSet rs = ...`) a my pracujeme s metodami, aniž bychom věděli, jaká konkrétní třída je "pod kapotou".