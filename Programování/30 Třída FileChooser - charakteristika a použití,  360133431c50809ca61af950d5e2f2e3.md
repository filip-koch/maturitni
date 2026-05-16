# 30. Třída FileChooser - charakteristika a použití, základní vlastnosti a metody (JavaFX)

---

### 1. Charakteristika a použití

Třída `FileChooser` slouží k zobrazení standardního systémového dialogu pro výběr souborů.

- **Účel:** Umožňuje uživateli vybrat soubor k otevření (Open) nebo určit název a umístění souboru k uložení (Save).
- **Vzhled:** Dialog vypadá stejně jako v operačním systému uživatele (Windows, macOS, Linux), což zvyšuje přívětivost aplikace.
- **Typ dat:** Výsledkem výběru je objekt třídy `java.io.File`, se kterým pak můžeme dále pracovat pomocí proudů (viz otázka č. 20).

### 2. Základní vlastnosti a metody

Před samotným zobrazením dialogu můžeme nastavit jeho chování:

| **Metoda** | **Popis** |
| --- | --- |
| **`setTitle(String title)`** | Nastaví titulek (text v horní liště) okna. |
| **`setInitialDirectory(File dir)`** | Určí, v jaké složce se má okno po otevření nacházet. |
| **`getExtensionFilters()`** | Vrací seznam filtrů, které omezují typy zobrazovaných souborů. |
| **`showOpenDialog(Window owner)`** | Zobrazí dialog pro **otevření** souboru a vrátí vybraný objekt `File`. |
| **`showSaveDialog(Window owner)`** | Zobrazí dialog pro **uložení** souboru a vrátí vybraný objekt `File`. |

### 3. Filtry přípon (Extension Filters)

Aby uživatel v seznamu nehledal mezi stovkami souborů, můžeme mu výběr omezit pouze na konkrétní přípony (např. `.txt`, `.png`).

- Používá se vnitřní třída `FileChooser.ExtensionFilter`.
- **Příklad:** `new FileChooser.ExtensionFilter("Textové soubory (*.txt)", "*.txt")`.

### 4. Zobrazení dialogu a zpracování výsledku

Dialog je tzv. **modální**, což znamená, že dokud ho uživatel nezavře, nemůže pracovat se zbytkem aplikace.

- Pokud uživatel výběr potvrdí, metoda vrátí objekt `File`.
- Pokud uživatel klikne na „Storno“ nebo okno zavře křížkem, metoda vrátí **`null`**. Na to je nutné v kódu pamatovat, abychom předešli chybě.

---

### Praktický příklad: Výběr souboru pro otevření

Java

```java
import javafx.stage.FileChooser;
import javafx.stage.Stage;
import java.io.File;

// V rámci Controlleru nebo metody start
public void vyberSoubor(Stage stage) {
    FileChooser fileChooser = new FileChooser();
    fileChooser.setTitle("Vyberte datový soubor"); // Nastavení titulku

    // Přidání filtru pro textové soubory
    fileChooser.getExtensionFilters().add(
        new FileChooser.ExtensionFilter("Text Files", "*.txt")
    );

    // Zobrazení dialogu a uložení výsledku
    File vybranySoubor = fileChooser.showOpenDialog(stage);

    if (vybranySoubor != null) {
        System.out.println("Cesta k souboru: " + vybranySoubor.getAbsolutePath());
    } else {
        System.out.println("Uživatel výběr zrušil.");
    }
}
```

---

### 5. Doplňkové info: Třída Alert (Vizuální odezva)

U maturity k této otázce často patří i zmínka o tom, jak informovat uživatele o výsledku (např. „Soubor byl úspěšně uložen“). K tomu slouží třída **`Alert`**.

- **Typy alertů:** `INFORMATION`, `WARNING`, `ERROR`, `CONFIRMATION`.
- **Metody:** `setTitle()`, `setHeaderText()`, `setContentText()` a nejdůležitější **`showAndWait()`**, která okno zobrazí a počká na reakci uživatele.

---

### 💡 Tahák pro maturanta (klíčové body):

- **`FileChooser`** není uzel (Node), který by se vkládal do layoutu, ale samostatné dialogové okno.
- **`showOpenDialog` vs `showSaveDialog`**: Liší se popisky tlačítek v okně a chováním k existujícím souborům.
- **`ExtensionFilter`** slouží k filtrování přípon (např. "*.jpg").
- **Ošetření `null`**: Vždy kontroluj, zda uživatel okno nezavřel bez výběru.
- **Propojení**: Získaný `File` se typicky předává třídám jako `FileReader` nebo `Scanner` pro čtení obsahu.