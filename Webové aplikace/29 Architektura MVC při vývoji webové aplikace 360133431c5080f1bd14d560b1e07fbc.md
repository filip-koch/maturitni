# 29. Architektura MVC při vývoji webové aplikace

---

### 1. Architektura MVC – Popis a princip

Hlavním cílem MVC je rozdělit kód do tří nezávislých vrstev, což usnadňuje údržbu a týmovou spolupráci.

- **Model (Model):** Reprezentuje datovou část a business logiku aplikace. Má na starosti práci s databází a veškeré výpočty.
- **View (Pohled):** Stará se o zobrazení dat uživateli. Obvykle jde o HTML šablony s minimem PHP kódu (pouze výpisy).
- **Controller (Kontroler):** Slouží jako prostředník (mozek aplikace). Přijímá požadavky od uživatele, volá příslušné modely a následně předává získaná data do pohledu.

---

### 2. Jádro aplikace a Směrovač (Router)

Aby celá aplikace fungovala jako celek, potřebuje „vstupní bránu“ a mechanismus řízení.

- **Jádro webové aplikace:** Centrální část, která celou aplikaci inicializuje a propojuje jednotlivé vrstvy.
- **Směrovač (Router):** Má za úkol analyzovat URL adresu (např. `/clanek/vypis`) a na jejím základě rozhodnout, který kontroler a jakou jeho metodu má spustit.
- **Využití dědičnosti:** Často se vytváří základní kontroler, ze kterého ostatní kontrolery dědí společné funkce (např. autorizaci uživatele).

---

### 3. Modely a práce s databází

V MVC architektuře je nepřípustné, aby s databází komunikoval přímo kontroler nebo pohled.

- **Zodpovědnost modelu:** Model obsahuje SQL dotazy a vrací zpracovaná data (pole nebo objekty).
- **Databázový wrapper:** Často se používá speciální třída, která obaluje přístup k databázi (např. přes PDO), aby byl kód bezpečnější a přehlednější.

---

### 4. Pohledy (Views)

Pohledy jsou zodpovědné za to, jak bude výsledek vypadat v prohlížeči.

- **Základní pohled (Layout):** Obsahuje společnou strukturu stránky (hlavička, menu, patička).
- **Dílčí pohledy:** Obsahují pouze specifický obsah pro danou stránku (např. formulář nebo tabulku), který se vkládá do základního pohledu.
- **Předávání dat:** Kontroler předává data do pohledu pomocí proměnných nebo asociativního pole, které pak pohled vypíše.

---

### Praktický příklad: Životní cyklus požadavku

Představ si, že uživatel chce vidět seznam článků:

1. **Uživatel** zadá URL `/clanky`.
2. **Směrovač** (Router) rozpozná adresu a zavolá `ClanekController`.
3. **Kontroler** požádá `ClanekModel` o data ze seznamu článků.
4. **Model** vytáhne data z databáze a vrátí je jako pole kontroleru.
5. **Kontroler** předá toto pole do **Pohledu** `vypis.php`.
6. **Pohled** vygeneruje HTML kód, který se pošle uživateli do prohlížeče.

---

### 💡 Tahák pro maturanta (klíčové body):

- **Model** = DATA (SQL, výpočty).
- **View** = VZHLED (HTML šablony).
- **Controller** = ŘÍZENÍ (logika, propojení).
- **Router** určuje, co se stane podle URL adresy.
- **Hlavní výhoda:** Oddělení zájmů – změna vzhledu neovlivní logiku aplikace a naopak.
- Pamatuj, že mezi modelem a pohledem **nikdy** neprobíhá přímá komunikace.