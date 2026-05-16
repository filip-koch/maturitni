# 18. Webové formuláře – struktura

---

### 1. Základní prvek `<form>` a jeho atributy

Každý formulář musí být uzavřen v párové značce `<form>`. Tato značka definuje, kam se data pošlou a jakým způsobem:

- **action:** URL adresa skriptu na serveru (např. v PHP), který data zpracuje.
- **method:** Způsob odeslání dat. Nejčastěji **GET** (data jsou vidět v URL, vhodné pro vyhledávání) nebo **POST** (data jsou skrytá v těle požadavku, bezpečnější, pro hesla nebo dlouhé texty).
- **enctype:** Nutné nastavit na `multipart/form-data`, pokud formulářem nahráváme soubory.

---

### 2. Prvek `<input>` a jeho typy

Prvek `<input>` je nejuniverzálnějším prvkem formuláře. Jeho chování určuje atribut `type`:

- **text:** Klasické jednořádkové pole pro jméno nebo adresu.
- **password:** Textové pole, které znaky maskuje (tečky/hvězdičky).
- **email / number / tel:** Speciální typy pro validaci (prohlížeč kontroluje správný formát).
- **checkbox:** Zaškrtávací políčko (lze vybrat více možností najednou).
- **radio:** Přepínač (v rámci jedné skupiny se stejným názvem lze vybrat jen jednu možnost).
- **submit:** Tlačítko, které formulář odešle na server.

---

### 3. Další formulářové prvky

Když `<input>` nestačí, používáme specializované značky:

- **`<textarea>`:** Pro víceřádkový text (např. komentář nebo zpráva).
- **`<select>` a `<option>`:** Vytváří rozbalovací seznam (dropdown menu).
- **`<button>`:** Univerzální tlačítko (může být typu `submit`, `reset` nebo jen `button` pro JavaScript).

---

### 4. Popisky a logické členění

Pro dobrou přístupnost (přístup pro nevidomé, ovládání na mobilu) jsou zásadní tyto prvky:

- **`<label>`:** Popisek prvku. Pomocí atributu `for` se propojuje s `id` daného vstupu. Kliknutí na label pak aktivuje samotné pole.
- **`<fieldset>` a `<legend>`:** Slouží k logickému seskupení souvisejících polí (např. "Osobní údaje") a jejich ohraničení rámečkem s nadpisem.

---

### 5. Důležité atributy prvků

Bez těchto atributů by formulář nefungoval správně:

- **name:** Naprosto klíčový atribut. Pod tímto jménem server (PHP) data přijímá (např. `$_POST['jmeno']`).
- **id:** Slouží k propojení s labelem nebo pro stylování v CSS.
- **value:** Předdefinovaná hodnota prvku.
- **placeholder:** Šedý nápovědný text uvnitř pole, který zmizí po začátku psaní.
- **required:** Zajistí, že pole musí být před odesláním vyplněno.
- **disabled:** Deaktivuje prvek (uživatel ho nemůže měnit).

---

### Praktický příklad: Registrační formulář

HTML

```html
<form action="zpracuj.php" method="post">
    <fieldset>
        <legend>Registrace uživatele</legend>
        
        <label for="uzivatel">Uživatelské jméno:</label>
        <input type="text" id="uzivatel" name="username" required placeholder="Zadejte jméno">

        <label for="heslo">Heslo:</label>
        <input type="password" id="heslo" name="password" required>

        <label>Pohlaví:</label>
        <input type="radio" name="pohlavi" value="muz" id="m"> <label for="m">Muž</label>
        <input type="radio" name="pohlavi" value="zena" id="z"> <label for="z">Žena</label>

        <button type="submit">Odeslat registraci</button>
    </fieldset>
</form>
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **`<form>`** musí mít `action` (kam) a `method` (jak).
- **Atribut `name`** je povinný pro odeslání dat na server – bez něj server neví, co je co.
- **`<label>`** zvyšuje přístupnost a komfort (propojení přes `for` a `id`).
- **Rozdíl mezi Checkbox a Radio:** Checkbox = více možností, Radio = právě jedna možnost.
- **HTML5 validace:** Atributy jako `required` nebo `type="email"` usnadňují kontrolu dat už u klienta.