# 26. Tvorba grafického rozhraní aplikací, Scene Builder (JavaFX)

---

### 1. Koncept FXML a oddělení logiky

Hlavním přínosem práce se Scene Builderem je dodržení návrhového vzoru **MVC (Model-View-Controller)**:

- **FXML (View):** XML soubor definující vzhled (kde je jaké tlačítko).
- **Controller (Controller):** Java třída, která obsahuje kód, co se má stát po kliknutí.
- **Model:** Data a logika aplikace.

### 2. Soubory v JavaFXML Application

Při tvorbě projektu s FXML se setkáš se třemi klíčovými soubory:

1. **`Main.java` (Application class):** Spouští aplikaci, vytváří `Stage` a pomocí třídy `FXMLLoader` načítá FXML soubor do scény.
2. **`Sample.fxml`:** Textový soubor (formát XML), který popisuje hierarchii komponent (vytváří ho Scene Builder).
3. **`Controller.java`:** Java třída propojená s FXML. Obsahuje metody obsluhy událostí (např. co udělá tlačítko).

### 3. Prostředí Scene Builder

Scene Builder je externí vizuální editor od společnosti Gluon (dříve Oracle). Pracuje se v něm stylem **Drag & Drop** (táhni a pusť).

**Základní části prostředí:**

- **Library (Knihovna):** Seznam všech dostupných komponent (Button, TextField, atd.).
- **Hierarchy (Hierarchie):** Stromová struktura prvků (vidíš, který prvek je v kterém kontejneru).
- **Content (Pracovní plocha):** Zde vidíš, jak rozhraní skutečně vypadá.
- **Inspector (Inspektor):** Nejdůležitější část, dělí se na:
    - *Properties:* Barvy, texty, fonty.
    - *Layout:* Velikosti, okraje (padding, margin).
    - *Code:* Zde se definuje **fx:id** a názvy metod pro události (např. `onAction`).

### 4. Propojení s kódem (Důležité pro maturitu!)

Aby mohl Controller ovládat prvky z FXML, používají se dvě věci:

1. **`fx:id`:** Unikátní identifikátor komponenty nastavený v Scene Builderu. V Controlleru pak vytvoříme proměnnou se stejným názvem označenou anotací `@FXML`.
2. **Event Handler (Obsluha událostí):** V Scene Builderu u tlačítka nastavíme do políčka `On Action` název metody (např. `tlacitkoKliknuto`). V Controlleru tuto metodu vytvoříme s anotací `@FXML`.

---

### Praktický příklad: Controller v Javě

Pokud máme v FXML tlačítko s `fx:id="btnPozdrav"` a nastavenou akcí `handleAkce`, kód bude vypadat takto:

Java

```java
import javafx.fxml.FXML;
import javafx.scene.control.Button;
import javafx.scene.control.Label;

public class Controller {

    @FXML
    private Button btnPozdrav; // Propojení s fx:id

    @FXML
    private Label lblVystup;

    @FXML
    private void handleAkce() { // Metoda pro On Action
        lblVystup.setText("Ahoj ze Scene Builderu!");
        btnPozdrav.setDisable(true); // Deaktivuje tlačítko
    }
}
```

---

### 5. Srovnání: Ruční psaní kódu vs. Scene Builder

| **Vlastnost** | **Ruční kód (Question 25)** | **Scene Builder (Question 26)** |
| --- | --- | --- |
| **Rychlost tvorby** | Pomalejší, nutné kompilovat pro náhled. | Velmi rychlá, okamžitý náhled. |
| **Přehlednost** | Logika a vzhled jsou promíchané. | Čisté oddělení (FXML vs. Java). |
| **Náročnost** | Nutná znalost hierarchie tříd JavaFX. | Intuitivní vizuální klikání. |

---

### 💡 Tahák pro maturanta (klíčové body):

- **FXML** je XML soubor definující grafiku.
- **Scene Builder** je grafický editor pro FXML.
- **fx:id** slouží k identifikaci prvku v kódu.
- **@FXML** je anotace v Javě, která propojuje proměnné a metody s FXML souborem.
- **Oddělení kódu:** Vzhled (FXML) se neupravuje v Javě, ale v editoru, což zpřehledňuje vývoj.