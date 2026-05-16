# 28. Komponenty ze skupiny Menu – charakteristika a použití, základní vlastnosti a události (JavaFX)

---

### 1. Hierarchie a struktura menu

U maturity je nejdůležitější vysvětlit, jak do sebe jednotlivé části zapadají. Menu v JavaFX není jedna komponenta, ale skládačka:

1. **MenuBar:** Hlavní horizontální lišta, která je obvykle umístěna v horní části okna.
2. **Menu:** Jednotlivá klikací slova v liště (např. „Soubor“, „Upravit“), která po kliknutí rozbalí seznam.
3. **MenuItem:** Konkrétní položky uvnitř rozbaleného menu, na které uživatel kliká pro vyvolání akce.

### 2. Charakteristika komponent

- **MenuBar:**
    - Slouží jako kontejner pro objekty typu `Menu`.
    - V `BorderPane` se nejčastěji umisťuje do horní části (`Top`).
- **Menu:**
    - Může obsahovat nejen položky, ale i další podmenu (Submenu).
    - Má vlastnost `text`, která definuje, co uživatel uvidí na liště.
- **MenuItem:**
    - Základní prvek pro spuštění příkazu (např. „Uložit“).
    - Reaguje na událost `onAction`.
- **Separator (SeparatorMenuItem):**
    - Vizuální vodorovná čára, která slouží k logickému oddělení skupin příkazů v rámci jednoho menu.

### 3. Speciální typy položek menu

Kromě klasických klikacích položek existují i ty, které si pamatují svůj stav:

- **CheckMenuItem:**
    - Položka s „fajfkou“. Funguje jako přepínač (zapnuto/vypnuto).
    - Vhodné pro nastavení (např. „Zobrazit mřížku“).
- **RadioMenuItem:**
    - Položka pro výběr právě jedné možnosti ze skupiny.
    - Podobně jako u RadioButtonu se tyto položky v kódu seskupují do **ToggleGroup**, aby bylo zajištěno, že může být vybrána vždy jen jedna.

### 4. Události a práce v Scene Builderu

- **Scene Builder:** Práce je velmi intuitivní. Přetáhneš `MenuBar` do layoutu, klikneš na něj a v sekci „Hierarchy“ můžeš přidávat další `Menu` a `MenuItem`.
- **Kód (Controller):** Aby menu něco dělalo, musí mít každá položka `MenuItem` nastavený název metody v sekci **On Action**.
    - *Pozor:* Samotné `Menu` (např. slovo „Soubor“) obvykle akci nemá, akce mají až jeho vnitřní položky.
- **Klávesové zkratky (Accelerators):** U maturity můžeš zmínit, že položkám lze přiřadit zkratky (např. Ctrl+S), což se v Scene Builderu nastavuje ve vlastnostech (Properties).

---

### Praktický příklad: Struktura v FXML / Controlleru

V Controlleru pak přistupujeme k položkám, které mají své `fx:id`, nebo přímo definujeme metody pro jejich kliknutí:

Java

```java
import javafx.fxml.FXML;
import javafx.scene.control.CheckMenuItem;

public class MenuController {

    @FXML
    private CheckMenuItem menuRezhim;

    @FXML
    private void handleUlozit() {
        System.out.println("Soubor byl uložen.");
    }

    @FXML
    private void handleZmenaRezhimu() {
        if (menuRezhim.isSelected()) {
            System.out.println("Tmavý režim zapnut.");
        } else {
            System.out.println("Tmavý režim vypnut.");
        }
    }
}
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **MenuBar** je lišta, **Menu** je kategorie, **MenuItem** je příkaz.
- **SeparatorMenuItem** slouží k vizuálnímu rozdělení položek.
- **CheckMenuItem** má stavy zapnuto/vypnuto.
- **RadioMenuItem** vyžaduje **ToggleGroup** pro výběr jedné možnosti.
- Hlavní událostí pro `MenuItem` je **`onAction`**.
- V `BorderPane` patří `MenuBar` vždy do sekce **Top**.