# 12. Tabulka – obecné a vyhledávací vlastnosti v návrhovém zobrazení, relace

---

### 1. Návrhové zobrazení tabulky (12a)

Návrhové zobrazení (Design View) je pracovní prostor, kde definujeme strukturu tabulky, nikoliv její data.

- **Definování polí:** Každý řádek v tomto zobrazení představuje jeden sloupec budoucí tabulky.
- **Datové typy:** Ke každému poli musíme přiřadit typ (např. Krátký text, Číslo, Datum a čas, Měna, Ano/Ne). To určuje, co Access do pole dovolí zapsat.
- **Vlastnosti pole:** Spodní část obrazovky se mění podle vybraného datového typu a umožňuje detailní nastavení.

### 2. Obecné vlastnosti polí (12b)

U zkoušky vysvětli tyto klíčové pojmy na příkladech:

- **Primární klíč (PK):** Pole, které jednoznačně identifikuje každý záznam (např. *ID_studenta*). Nesmí být prázdné ani duplicitní.
- **Velikost pole (Field Size):** Omezuje počet znaků (u textu) nebo určuje rozsah čísel (u čísel).
    - *Příklad:* Pro PSČ stačí velikost 5 znaků.
- **Formát (Format):** Určuje, jak se data zobrazují, aniž by se změnila jejich hodnota.
    - *Příklad:* Datum zobrazené jako „Středa, 10. května“.
- **Vstupní maska (Input Mask):** Vynucuje konkrétní tvar zadávání dat.
    - *Příklad:* `000\ 000\ 000` pro telefonní číslo zajistí, že uživatel napíše jen číslice v tomto formátu.
- **Titulky (Caption):** Uživatelsky čitelný název pole. Pokud se pole jmenuje technicky `prijm_zam`, v titulku může být hezky „Příjmení“.
- **Ověřovací pravidlo (Validation Rule):** Podmínka, kterou musí data splnit, aby byla uložena.
    - *Příklad:* `>0` pro cenu nebo `<Datum()` pro datum narození (člověk se nemohl narodit v budoucnu).

### 3. Vyhledávací vlastnosti (12b)

Slouží k vytvoření **výklopného seznamu (Combo Box)** přímo v buňce tabulky.

- Místo ručního vypisování (např. názvu třídy) si uživatel vybere ze seznamu.
- Data mohou pocházet z jiné tabulky nebo z pevně zadaného seznamu hodnot.
- **Význam:** Zvyšuje rychlost zadávání a eliminuje překlepy.

### 4. Relace (Relace mezi tabulkami)

Relace jsou logické vazby, které spojují data z různých tabulek přes **primární** a **cizí klíč**.

- V MS Access se spravují v samostatném okně **Relace**.
- **Referenční integrita:** Klíčová funkce, která hlídá logiku spojení. Pokud je zapnutá, Access nedovolí smazat záznam (např. školu), pokud na něj odkazují jiné záznamy (např. žáci v této škole).

---

### 💡 **Tahák pro maturanta (klíčové body):**

- **Návrhové zobrazení** = tvorba „kostry“ tabulky (Pole + Typy).
- **Klíče:** Primární klíč musí být unikátní.
- **Vstupní maska** hlídá formát (vzhled při psaní), **Ověřovací pravidlo** hlídá hodnotu (logiku).
- **Vyhledávací pole** nabízejí seznam hodnot (Combo Box) pro snadnější zápis.
- **Relace** propojují tabulky; **Referenční integrita** zabraňuje vzniku „osiřelých“ záznamů.