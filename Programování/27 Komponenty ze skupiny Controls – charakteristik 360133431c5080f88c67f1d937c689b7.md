# 27. Komponenty ze skupiny Controls – charakteristika a použití, základní vlastnosti a události  (JavaFX)

---

### 1. Charakteristika skupiny Controls

Komponenty ze skupiny **Controls** jsou interaktivní prvky, které umožňují uživateli komunikovat s aplikací (zadávat text, vybírat možnosti, klikat na tlačítka). Všechny tyto prvky dědí ze společného předka `Control`.

### 2. Interaktivní tlačítka a přepínače

- **Button (Tlačítko):**
    - Základní prvek pro vyvolání akce.
    - Metoda `setText(String text)` nastaví nápis na tlačítku.
- **CheckBox (Zaškrtávací pole):**
    - Umožňuje uživateli vybrat více nezávislých možností najednou.
    - Metoda `setSelected(boolean selected)` nastaví pole jako zaškrtnuté nebo nezaškrtnuté.
    - Metoda `getText()` vrátí popisek pole.
- **RadioButton (Přepínač):**
    - Slouží k výběru právě **jedné** možnosti ze skupiny.
    - Aby fungovalo logické seskupení (výběr jednoho zruší ostatní), musí být přiřazeny do třídy **`ToggleGroup`**.
    - Metoda `getSelectedToggle()` u třídy `ToggleGroup` vrací aktuálně zvolený přepínač.

### 3. Textové komponenty

- **Label (Popisek):**
    - Slouží k zobrazení statického textu, který uživatel nemůže měnit.
    - Metody `setText()` a `getText()` pro manipulaci s obsahem.
- **TextField (Textové pole):**
    - Jednořádkový vstup pro text (např. pro jméno nebo heslo).
    - Metoda `getText()` načte to, co uživatel napsal.
- **TextArea (Textová oblast):**
    - Víceřádkový vstup nebo výstup pro delší texty.
    - Metoda `appendText(String text)` přidá text na konec stávajícího obsahu.
    - Metoda `clear()` vymaže veškerý text.
    - Metoda `deleteText(int start, int end)` odstraní text mezi zadanými indexy.

### 4. Komponenty pro výběr ze seznamu

- **ListView (Seznam):**
    - Zobrazuje svislý seznam položek, ve kterém lze rolovat.
    - Položky jsou uloženy v **`ObservableList`**, který získáme metodou `getItems()`.
    - Metoda `getSelectionModel()` umožňuje zjistit, která položka je vybraná (např. pomocí `selectFirst()` nebo `getSelectedItem()`).
- **ComboBox (Rozbalovací seznam):**
    - Kompaktní prvek, který se rozbalí až po kliknutí.
    - Metoda `getValue()` vrátí aktuálně vybranou položku.
    - Metoda `setItems(ObservableList<T> items)` naplní seznam daty.
- **ColorPicker (Výběr barvy):**
    - Specializovaná komponenta, která otevře dialog pro výběr barvy.
    - Metoda `getValue()` vrátí vybranou barvu jako objekt typu `Color`.

### 5. Události a vlastnosti

U všech těchto komponent je nejdůležitější událostí **`On Action`**.

- V Scene Builderu určíme název metody, která se má spustit (např. při kliknutí na tlačítko nebo výběru barvy).
- V kódu Javy pak tuto metodu označíme anotací `@FXML`.

---

### 💡 Tahák pro maturanta (klíčové body):

- **Button/CheckBox/RadioButton:** Interakce a volby. Pamatuj na `ToggleGroup` pro RadioButtony.
- **TextField vs TextArea:** Jednořádkový vs víceřádkový vstup.
- **Data v seznamech:** Pro `ListView` i `ComboBox` používáme rozhraní **`ObservableList`**.
- **Zřetězení metod:** U výběrových modelů se často píše např. `getSelectionModel().getSelectedItem()`.
- **Getter/Setter:** Skoro každá komponenta má `getText()` a `setText()`.