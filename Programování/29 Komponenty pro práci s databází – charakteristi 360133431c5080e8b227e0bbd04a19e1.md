# 29. Komponenty pro práci s databází – charakteristika a použití, základní vlastnosti a události (JavaFX)

---

### 1. Princip zobrazení databázových dat v JavaFX

V JavaFX nepíšeme data do tabulky "ručně" řádek po řádku jako text. Místo toho využíváme mechanismus **Data Bindingu**.

- **Model:** Máme seznam dat (obvykle `ObservableList`), který je propojen s tabulkou.
- **Automatizace:** Jakmile se změní data v tomto seznamu, tabulka se automaticky překreslí.
- **Propojení:** Mezi databází a tabulkou stojí kód, který provede `SELECT`, vytvoří objekty a naplní jimi seznam .

### 2. Hlavní komponenty pro tabulky

Pro zobrazení dat používáme hierarchii tříd:

### A) TableView

- Je to hlavní kontejner pro celou tabulku.
- **`setItems(ObservableList items)`**: Nejdůležitější metoda, která propojí tabulku se zdrojem dat.
- **`getSelectionModel()`**: Umožňuje zjistit, který řádek uživatel vybral.
- **`refresh()`**: Vynutí překreslení tabulky, pokud se data změnila externě.

### B) TableColumn

- Reprezentuje jeden konkrétní sloupec v tabulce.
- Každý sloupec musí vědět, kterou vlastnost (atribut) z datového objektu má zobrazovat. K tomu slouží **`CellValueFactory`**.
- **`setText(String label)`**: Nastaví nadpis sloupce.

### C) TableCell

- Reprezentuje jednu konkrétní buňku na průsečíku řádku a sloupce.
- JavaFX umožňuje upravit vzhled buněk pomocí **`CellFactory`** (např. pokud je číslo záporné, obarvi buňku červeně).

### 3. Připojení a plnění daty

Při práci s databází postupujeme následovně:

1. **Navázání spojení:** Pomocí `DriverManager.getConnection()`.
2. **Získání výsledků:** Spustíme `SELECT` a získáme `ResultSet` .
3. **Dynamická tvorba sloupců:** Pokud předem neznáme strukturu, můžeme sloupce vytvořit v cyklu podle metadat z databáze (`getColumnName`) .
4. **Naplnění seznamu:** Procházíme `ResultSet` a přidáváme řádky do `ObservableList` .

---

### Praktický příklad: Naplnění TableView z databáze

Tento kód ukazuje, jak se data z ResultSetu "přelijí" do tabulky:

Java

```java
// Definice tabulky a dat v Controlleru
@FXML private TableView<ObservableList<String>> tvData;
private ObservableList<ObservableList<String>> data = FXCollections.observableArrayList();

// Metoda pro načtení
public void nactiData(ResultSet rs) throws SQLException {
    data.clear(); // Vymazání starých dat [cite: 171]
    
    // Procházení řádků z databáze [cite: 185]
    while (rs.next()) {
        ObservableList<String> radek = FXCollections.observableArrayList();
        for (int i = 1; i <= rs.getMetaData().getColumnCount(); i++) {
            radek.add(rs.getString(i)); // Přidání hodnoty z každého sloupce [cite: 189]
        }
        data.add(radek); // Přidání celého řádku do seznamu pro tabulku [cite: 191]
    }
    
    tvData.setItems(data); // Propojení seznamu s komponentou TableView [cite: 193]
}
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **`TableView`** je vizuální prvek, **`ObservableList`** je jeho datový motor.
- **`requires java.sql;`** musí být v `module-info.java` pro přístup k databázovým třídám.
- **`TableColumn`** potřebuje `CellValueFactory`, aby věděl, co má zobrazit.
- **Dynamické tabulky:** Počet sloupců a jejich jména lze zjistit za běhu pomocí `resultSet.getMetaData()` .
- **Interaktivita:** Přes `getSelectionModel().getSelectedItem()` získáme data z řádku, na který uživatel klikl .