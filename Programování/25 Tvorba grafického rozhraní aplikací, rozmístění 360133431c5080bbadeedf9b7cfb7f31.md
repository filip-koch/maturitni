# 25. Tvorba grafického rozhraní aplikací, rozmístění (JavaFX)

---

### 1. Charakteristika JavaFX

JavaFX je moderní knihovna pro tvorbu grafických aplikací v Javě, která nahradila starší Swing. Umožňuje vytvářet vizuálně bohatá rozhraní s podporou CSS (pro stylování) a FXML (pro definici vzhledu v XML).

### 2. Architektura JavaFX aplikace (Divadelní analogie)

Pro snadné zapamatování se v JavaFX používá terminologie z divadelního prostředí:

- **Stage (Jeviště/Stupeň):** Představuje hlavní okno aplikace. V aplikaci může být více oken, ale jedno je obvykle hlavní (`primaryStage`).
- **Scene (Scéna):** Představuje konkrétní obsah okna. Stage může v čase měnit scény (např. přepnutí z menu do hry).
- **Scene Graph (Graf scény):** Stromová struktura všech prvků (uzlů) v aplikaci.
- **Nodes (Uzly):** Jednotlivé prvky grafického rozhraní (tlačítka, popisky, kontejnery).

### 3. Struktura JavaFX projektu

Hlavní třída aplikace musí dědit od třídy `javafx.application.Application`. Životní cyklus má tyto fáze:

1. **`main()`**: Zavolá statickou metodu `launch(args)`, která spustí JavaFX vlákno.
2. **`start(Stage stage)`**: Hlavní vstupní bod, kde programátor nastavuje scénu a zobrazuje okno.
3. **`stop()`**: Volá se při ukončení aplikace.

### 4. Rozmístění prvků (Layouts)

V JavaFX nepoužíváme absolutní souřadnice (např. "tlačítko na pixelu [10, 20]"), protože okno se může zvětšovat. Používáme **Layout Panes** (kontejnery), které automaticky organizují prvky v nich obsažené:

- **`VBox` (Vertical Box):** Skládá prvky pod sebe do jednoho sloupce.
- **`HBox` (Horizontal Box):** Skládá prvky vedle sebe do jedné řady.
- **`BorderPane`:** Rozděluje okno na 5 oblastí (Top, Bottom, Left, Right, Center). Ideální pro hlavní okno aplikace s menu nahoře a status barem dole.
- **`GridPane`:** Uspořádá prvky do mřížky (řádky a sloupce). Prvek může zabírat i více buněk.
- **`AnchorPane`:** Umožňuje "ukotvit" prvky k okrajům kontejneru (např. tlačítko vždy v pravém dolním rohu).
- **`StackPane`:** Skládá prvky na sebe (jako hromadu karet), užitečné pro text přes obrázek.

### 5. Práce s komponentami

Komponenty (ovládací prvky) vkládáme do layoutů. Mezi základní patří:

- `Button` (Tlačítko), `Label` (Textový popisek), `TextField` (Jednořádkový vstup).
- Všechny komponenty mají metody jako `setText()` nebo `getText()`.

---

### Praktický příklad: Jednoduchá aplikace v kódu

Java

```java
import javafx.application.Application;
import javafx.scene.Scene;
import javafx.scene.control.Button;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class MojeApp extends Application {
    @Override
    public void start(Stage primaryStage) {
        // 1. Vytvoření komponenty
        Button btn = new Button("Klikni na mě");

        // 2. Vytvoření Layoutu a vložení komponenty
        VBox layout = new VBox(); 
        layout.getChildren().add(btn);

        // 3. Vytvoření Scény s layoutem (velikost 300x250)
        Scene scene = new Scene(layout, 300, 250);

        // 4. Nastavení Stage
        primaryStage.setTitle("Moje první JavaFX okno");
        primaryStage.setScene(scene);
        primaryStage.show(); // Zobrazení okna
    }

    public static void main(String[] args) {
        launch(args);
    }
}
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Stage** = okno, **Scene** = obsah, **Node** = prvek.
- Aplikace vždy dědí od **`Application`** a implementuje metodu **`start()`**.
- **Layouty** jsou nutné pro responzivní design (přizpůsobení velikosti okna).
- Pamatuj si rozdíl mezi **VBox** (sloupec) a **HBox** (řádek).
- **Scene Graph** je hierarchie prvků (strom), kde kořenem (root) je obvykle nějaký Layout Pane.