# 19. Webové formuláře – vzhled

---

### 1. Atributové selektory

Vzhledem k tomu, že většina formulářových prvků používá stejnou značku `<input>`, musíme v CSS rozlišovat mezi jejich typy pomocí atributových selektorů.

- **Význam:** Umožňují vybrat prvek na základě přítomnosti nebo hodnoty jeho HTML atributu.
- **Zápis:** Používají se hranaté závorky `[]`.
- **Příklady:**
    - `input[type="text"]` – vybere pouze jednořádková textová pole.
    - `input[type="submit"]` – vybere odesílací tlačítko.
    - 

`input[name="email"]` – vybere prvek s konkrétním jménem.

---

### 2. Pseudotřídy pro stavy formulářů

Pseudotřídy nám umožňují měnit vzhled prvků dynamicky podle toho, co s nimi uživatel dělá nebo v jakém stavu se data nacházejí:

- **`:focus`**: Aktivuje se, když uživatel do pole klikne nebo do něj přejde tabulátorem (vhodné pro zvýraznění aktivního pole).
- **`:required` a `:optional`**: Rozlišuje pole, která jsou povinná, od těch volitelných.
- **`:valid` a `:invalid`**: Reaguje na automatickou validaci prohlížeče (např. pokud je v poli pro e-mail chybný formát, pole zčervená).
- **`:checked`**: Používá se pro stylování zaškrtnutých checkboxů nebo vybraných radio buttonů.
- **`:disabled`**: Definuje vzhled prvků, které jsou momentálně neaktivní a nelze do nich psát.

---

### 3. Pokročilé selektory pro vazby prvků

Často potřebujeme stylovat prvky v závislosti na jejich okolí (např. popisek vedle zaškrtnutého pole).

- **Přímý potomek (`>`)**: Vybere prvek, který je bezprostředně uvnitř jiného prvku (např. `fieldset > input`).
- **Následník (`+`)**: Vybere prvek, který následuje ihned za jiným prvkem na stejné úrovni.
    - *Využití:* `input:checked + label` (umožňuje zvýraznit text u zaškrtnutého políčka).

---

### Praktická ukázka: Interaktivní formulář

CSS

```css
/* Základní vzhled textových polí */
input[type="text"], 
input[type="email"] {
    border: 1px solid #ccc;
    padding: 8px;
    width: 100%;
}

/* Zvýraznění aktivního pole */
input:focus {
    border-color: blue;
    background-color: #f0f8ff;
    outline: none;
}

/* Indikace chyby při psaní */
input:invalid {
    border-color: red;
}

/* Stylování popisku u zaškrtnutého checkboxu */
input[type="checkbox"]:checked + label {
    font-weight: bold;
    color: green;
}
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Atributové selektory** (`[type="..."]`) jsou nezbytné pro odlišení různých inputů.
- **`:focus`** je nejdůležitější pseudotřída pro uživatelskou přívětivost (UX).
- **Validace v reálném čase:** Pomocí `:valid` a `:invalid` dáváme uživateli okamžitou zpětnou vazbu.
- **Selektor následníka (`+`)** je trik, jak stylovat texty (`label`) na základě stavu formulářového pole.
- **Zpřístupnění:** Při stylování (zejména u `:focus`) nikdy neodstraňuj `outline` bez náhrady jiným vizuálním prvkem, aby lidé ovládající web klávesnicí věděli, kde se nacházejí.