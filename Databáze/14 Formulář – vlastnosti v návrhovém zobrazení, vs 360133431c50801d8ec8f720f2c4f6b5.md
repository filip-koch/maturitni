# 14. Formulář – vlastnosti v návrhovém zobrazení, vstupní formulář, makra

---

### 1. Návrhové zobrazení a jeho složky (14a, 14b)

Návrhové zobrazení je prostor, kde formulář vytváříme a upravujeme jeho vzhled.

- **Návrhová mřížka:** Slouží k přesnému umisťování ovládacích prvků.
- **Souprava nástrojů:** Obsahuje prvky, které na formulář vkládáme (textová pole, popisky, tlačítka, seznamy).
- **Seznam polí:** Okno, ze kterého přetahujeme konkrétní sloupce z tabulek přímo na plochu formuláře.
- **Sekce formuláře:** Formulář se dělí na tři základní části:
    - **Záhlaví formuláře:** Zde bývá obvykle název formuláře nebo logo.
    - **Detail:** Hlavní část, kde se zobrazují samotná data a pole k vyplnění.
    - **Zápatí formuláře:** Místo pro součty nebo ovládací tlačítka.

### 2. Typy formulářů a jejich vlastnosti (14a, 14c)

V Accessu můžeme nastavit, jakým způsobem se budou záznamy zobrazovat:

- **Samostatný formulář:** Zobrazuje vždy pouze jeden záznam na celé ploše.
- **Nekonečný (souvislý) formulář:** Zobrazuje více záznamů pod sebou, podobně jako tabulka, ale s grafickými prvky formuláře.
- **Formulář s podformulářem:** Používá se pro zobrazení dat z propojených tabulek (vztah 1:N). Například v hlavním formuláři je „Zákazník“ a v podformuláři je seznam jeho „Objednávek“.

### 3. Vstupní formulář a editace dat (14d, 14e)

Vstupní formulář je speciálně upravený tak, aby sloužil primárně pro zápis nových dat.

- **Vlastnosti pro vkládání:** Lze nastavit vlastnost „Zadávání dat“ na Ano, což způsobí, že se po otevření zobrazí prázdný formulář připravený pro nový záznam.
- **Textová pole a popisky:** Slouží k editaci a popisu dat. Textové pole je „živé“ (propojené s daty), popisek je statický text.
- **Výpočty:** Ve formulářích lze vytvářet nová pole, která obsahují vzorce (např. výpočet věku z data narození nebo celková cena položky).

### 4. Makra a automatizace (14a)

Makra slouží k automatizaci jednoduchých úkolů bez nutnosti programování.

- **Příklad:** Tlačítko, které po kliknutí otevře jiný formulář, vytiskne sestavu nebo zavře aktuální okno.
- Makra se na formulář obvykle vážou přes **Události** (např. „Při kliknutí“ na tlačítko).

---

### 💡 **Tahák pro maturanta (klíčové body):**

- **Formulář** je „pohledná maska“ nad tabulkou pro uživatele.
- **Sekce:** Záhlaví (název), Detail (data), Zápatí (tlačítka/součty).
- **Podformulář** slouží k zobrazení souvisejících dat (1:N).
- **Výpočty** se píší do textových polí jako výrazy začínající rovnítkem.
- **Vstupní formulář** je nastaven tak, aby hned nabízel prázdné pole pro nový záznam.