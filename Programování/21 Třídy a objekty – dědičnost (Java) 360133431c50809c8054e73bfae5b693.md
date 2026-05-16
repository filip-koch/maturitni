# 21. Třídy a objekty – dědičnost (Java)

---

### 1. Dědičnost (Inheritance)

Dědičnost je mechanismus, který umožňuje vytvořit novou třídu (potomka) na základě již existující třídy (předka).

- **Vztah „je-a“ (is-a):** Potomek je speciálnějším typem předka (např. *Pes* je *Zvíře*, *Student* je *Člověk*).
- **Klíčové slovo `extends`:** Používá se v hlavičce třídy k definování dědičnosti.
- **Vlastnosti:** Potomek automaticky přebírá všechny atributy a metody předka (pokud nejsou soukromé) a může přidávat své vlastní nebo měnit chování těch stávajících.
- **Single Inheritance:** V Javě může třída dědit pouze z **jednoho** přímého předka.

### 2. Dědičnost vs. Kompozice

U maturity je důležité tyto dva přístupy rozlišit:

- **Dědičnost (is-a):** Třída rozšiřuje jinou třídu. Používáme ji, když potomek skutečně náleží do stejné kategorie.
- **Kompozice (has-a):** Třída obsahuje jinou třídu jako svůj atribut (např. *Auto* má *Motor*). Je to vztah „má-a“. Kompozice je často flexibilnější než dědičnost.

### 3. Konstruktory v dědičnosti a slovo `super`

Konstruktory se nedědí. Při vytvoření instance potomka se však musí vždy jako první zavolat konstruktor předka.

- **Klíčové slovo `super`:** Slouží k volání konstruktoru předka nebo jeho metod.
- **Pravidlo:** Volání `super()` musí být **prvním příkazem** v konstruktoru potomka. Pokud ho nenapíšete, Java se pokusí automaticky zavolat bezparametrický konstruktor předka.

### 4. Přístupová práva v dědičnosti

Určují, co potomek ze svého předka „uvidí“:

- **`private`:** Potomek k těmto prvkům nemá přístup (jsou skryté uvnitř předka).
- **`protected`:** Ideální pro dědičnost. Prvky jsou přístupné v rámci balíčku a ve všech potomcích (i v jiných balíčcích).
- **`public`:** Přístupné odevšad.

### 5. Klíčové slovo `final`

Klíčové slovo `final` slouží k omezení dědičnosti:

1. **`final` třída:** Z této třídy již nelze dále dědit (např. třída `String` v Javě).
2. **`final` metoda:** Tuto metodu potomek nemůže překrýt (změnit její tělo).
3. **`final` proměnná:** Funguje jako konstanta – její hodnotu nelze po první inicializaci změnit.

---

### Praktický příklad: Dědičnost v akci

Java

```java
// Předek (Superclass)
class Zvire {
    protected String jmeno;

    public Zvire(String jmeno) {
        this.jmeno = jmeno;
    }

    public void vydasvuk() {
        System.out.println("Zvíře vydává neurčitý zvuk.");
    }
}

// Potomek (Subclass)
class Pes extends Zvire {
    public Pes(String jmeno) {
        super(jmeno); // Volání konstruktoru předka
    }

    @Override // Překrytí metody předka
    public void vydasvuk() {
        System.out.println(jmeno + " štěká: Haf haf!");
    }
}
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **`extends`** = klíčové slovo pro dědičnost.
- **`super()`** = volání konstruktoru předka (musí být na 1. řádku).
- **`@Override`** = anotace, která říká, že přepisujeme metodu předka.
- **`protected`** = nejdůležitější modifikátor pro dědičnost – vidí potomek, ale ne cizí třídy.
- **`final`** = stopka pro dědění nebo přepisování.
- **Všechny třídy** v Javě automaticky dědí z kořenové třídy **`Object`**.