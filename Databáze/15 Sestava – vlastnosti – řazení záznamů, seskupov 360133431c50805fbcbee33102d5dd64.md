# 15. Sestava – vlastnosti – řazení záznamů, seskupování da

---

### 1. Charakteristika a vzhled sestavy (15a)

Sestava slouží k prezentaci dat z tabulek nebo dotazů v profesionálně formátované a přehledné podobě. Na rozdíl od formulářů jsou data v sestavě primárně určena ke čtení, nikoliv k editaci.

**Základní prvky návrhu:**

- **Návrhové zobrazení:** Hlavní pracovní prostor pro definici struktury a vlastností.
- **Souprava nástrojů:** Obsahuje ovládací prvky jako textová pole (pro data), popisky (pro názvy), čáry nebo obrázky.
- **Návrhová mřížka:** Pomáhá s přesným zarovnáním prvků na ploše sestavy.
- **Seznam polí:** Nabídka dostupných sloupců ze zdroje dat (tabulky nebo dotazu), které lze přetáhnout do sestavy.

### 2. Sekce sestavy (15a)

Sestava má bohatší strukturu než formulář, protože musí řešit logické celky dat a stránkování:

- **Záhlaví / Zápatí sestavy:** Objevuje se pouze **jednou** v celém dokumentu (např. titulní strana nebo celkový součet na konci).
- **Záhlaví / Zápatí stránky:** Opakuje se na **každé vytištěné stránce** (např. názvy sloupců nahoře a číslo stránky dole).
- **Záhlaví / Zápatí skupiny:** Vznikne automaticky při zapnutí seskupování; obsahuje název skupiny a mezisoučty za danou skupinu.
- **Detail:** Zde se vypisují jednotlivé záznamy (řádky) z databáze.

### 3. Řazení a seskupování dat (15a, 15b)

Seskupování a řazení dává sestavě přehlednou hierarchii:

- **Řazení:** Určuje pořadí záznamů (např. abecedně podle příjmení nebo od nejlevnějšího zboží).
- **Seskupování:** Sdružuje záznamy se stejnou hodnotou do logických bloků.
    - *Příklad:* Sestava zaměstnanců seskupená podle **oddělení**. Uvidíme nadpis "Marketing", pod ním seznam lidí, pak nadpis "IT" atd.

### 4. Výpočty a průběžné součty (15b)

Sestavy jsou ideální pro statistické přehledy díky automatizovaným výpočtům:

- **Výpočty pro skupiny:** V zápatí skupiny můžeme pomocí funkcí (např. `Suma`) spočítat hodnotu jen za daný blok (např. tržby za konkrétní oddělení).
- **Průběžné součty:** Speciální vlastnost textového pole, která postupně přičítá hodnoty řádek po řádku, takže uživatel vidí narůstající celkovou částku v průběhu sestavy.

---

💡 **Tahák pro maturanta (klíčové body):**

- **Sestava** je neměnný výstup určený pro tisk nebo export.
- **Struktura sekcí:** Záhlaví sestavy (1x), Záhlaví stránky (všude), Záhlaví skupiny (začátek bloku), Detail (data), Zápatí (souhrny).
- **Seskupování** rozděluje data do logických celků (např. podle města, kategorie).
- **Výpočty** se nejčastěji umisťují do **Zápatí skupiny** (pro mezisoučet) nebo **Zápatí sestavy** (pro celkový součet dokumentu).
- **Průběžný součet** (Running Sum) kumuluje hodnoty od prvního řádku až po poslední.