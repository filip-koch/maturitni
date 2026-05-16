# 8. Operátory (C, Java)

---

### 1. Definice operátoru

Operátor je speciální symbol, který provádí určitou operaci s jedním nebo více operandy (daty/proměnnými).

- **Unární operátory:** Pracují s jedním operandem (např. `x`, `++i`).
- **Binární operátory:** Pracují se dvěma operandy (např. `a + b`).
- **Ternární operátor:** Pracuje se třemi operandy (existuje pouze jeden: `? :`).

### 2. Rozdělení operátorů podle funkce

U zkoušky je dobré rozdělit operátory do logických skupin:

### A) Aritmetické operátory

Slouží pro matematické výpočty:

- `+`, , , `/` (všimněte si, že u celých čísel v C i Javě probíhá **celočíselné dělení**).
- `%` (modulo) – zbytek po celočíselném dělení.
- `++`, `-` (inkrementace a dekrementace) – zvýšení/snížení hodnoty o 1.
    - *Prefix* (`++i`): Nejdříve se změní hodnota, pak se s ní pracuje.
    - *Postfix* (`i++`): Nejdříve se pracuje s původní hodnotou, pak se změní.

### B) Relační operátory

Slouží k porovnávání hodnot. Výsledkem je logická hodnota (v Javě `boolean`, v C číslo 0/1).

- `==` (rovnost), `!=` (nerovnost), `>`, `<`, `>=`, `<=`.

### C) Logické operátory

Slouží ke spojování více podmínek:

- `&&` (logické A – AND): Platí, pokud jsou obě podmínky pravdivé.
- `||` (logické NEBO – OR): Platí, pokud je alespoň jedna podmínka pravdivá.
- `!` (logická negace – NOT): Obracejí pravdivost.

### D) Přiřazovací operátory

- `=` (základní přiřazení).
- Složené operátory: `+=`, `=`, `=`, `/=`, `%=`. Např. `a += 5` je totéž jako `a = a + 5`.

### 3. Ternární operátor

Jediný operátor se třemi operandy. Funguje jako zkrácený zápis podmínky `if-else`.

- **Syntaxe:** `podmínka ? hodnota_pokud_pravda : hodnota_pokud_nepravda;`
- **Příklad:** `max = (a > b) ? a : b;` (do `max` se uloží větší z čísel).

### 4. Priorita a asociativita operátorů

Určuje, v jakém pořadí se operace v jednom výrazu provádějí.

- **Priorita:** Násobení má přednost před sčítáním. Závorky mají absolutně nejvyšší prioritu.
- **Asociativita:** Určuje směr vyhodnocování u operátorů se stejnou prioritou (většinou zleva doprava, ale např. přiřazení `=` jde zprava doleva).

---

### Rozdíly mezi C a Java (Důležité u maturity!)

- **Typ výsledku:** V Javě relační a logické operátory vrací striktně typ `boolean`. V C vrací `int` (0 pro nepravdu, nenulové pro pravdu).
- **Zkrácené vyhodnocování (Short-circuit):** Oba jazyky u `&&` a `||` vyhodnocují pouze to, co je nutné. Pokud u `&&` první část neplatí, druhou už počítač ani nezkoumá.

---

### 💡 Tahák pro maturanta (klíčové body):

- **Modulo (`%`)** funguje pouze s celými čísly.
- **Rovnost se píše `==`**, nikoliv `=`, což je častá chyba.
- **Inkrementace `++`** je nejrychlejší způsob, jak přičíst jedničku.
- **Závorky** používejte vždy, když si nejste jistí prioritou – kód je pak čitelnější.
- **Logické spojky:** `&&` má vyšší prioritu než `||`.