# 20. Webová aplikace – princip, jazyky a technologie

---

### 1. Webová aplikace – pojem a princip fungování

Webová aplikace je softwarová aplikace, která neběží přímo v operačním systému počítače, ale na vzdáleném webovém serveru a uživatel k ní přistupuje skrze webový prohlížeč.

- **Rozdíl oproti statickému webu:** Zatímco statický web zobrazuje všem uživatelům stejný soubor (HTML), webová aplikace obsah generuje dynamicky na základě požadavků uživatele, dat v databázi nebo přihlášeného profilu.
- **Princip Client-Server:**
    
    1. **Klient (prohlížeč)** odešle požadavek (HTTP Request).
    2.  **Server** požadavek přijme, skript (např. v PHP) ho zpracuje, případně komunikuje s databází.
    3.  **Server** odešle výsledek (HTTP Response) – obvykle ve formátu HTML, CSS a JS, kterému prohlížeč rozumí.
    

---

### 2. Struktura webové aplikace (Vrstvy a architektury)

Moderní webové aplikace se obvykle dělí do tří logických vrstev, což usnadňuje vývoj a údržbu:

1. **Prezenční vrstva (Front-end):** To, co uživatel vidí a s čím interaguje v prohlížeči.
2. **Logická vrstva (Back-end):** "Mozeček" aplikace běžící na serveru, který zpracovává data a řídí funkčnost.
3. **Datová vrstva (Databáze):** Místo, kde jsou data trvale uložena (uživatelé, články, objednávky).

Často se v této souvislosti zmiňuje architektura **MVC** (Model-View-Controller), která tyto vrstvy striktně odděluje.

---

### 3. Jazyky a technologie

Pro každou vrstvu používáme jiné nástroje:

- **Na straně klienta (Front-end):**
    - **HTML:** Struktura obsahu.
    - **CSS:** Vzhled a rozvržení.
    - **JavaScript:** Interaktivita a logika na straně uživatele.
- **Na straně serveru (Back-end):**
    - **PHP:** Velmi rozšířený jazyk pro web (např. WordPress).
    - **Další možnosti:** Python, Node.js (JavaScript na serveru), Ruby, Java nebo C#.
- **Databázové systémy: - případně soubory**
    - **Relační (SQL):** MySQL, MariaDB, PostgreSQL.
    - **Nerelační (NoSQL):** MongoDB (pro specifické typy dat).

---

### 4. Architektury (Monolit vs. API)

U maturity můžeš zmínit dva hlavní přístupy k tvorbě:

- **Tradiční (Monolit):** Server vygeneruje kompletní HTML stránku a tu pošle prohlížeči (časté u PHP aplikací).
- **Moderní (SPA - Single Page Application):** Server posílá pouze surová data (často formát JSON) a o vykreslení celé stránky se stará JavaScript přímo u klienta (např. pomocí frameworků React nebo Vue).

---

### 💡 Tahák pro maturanta (klíčové body):

- **Webová aplikace** generuje obsah dynamicky na serveru.
- **Client-Server model:** Základem je cyklus Požadavek (Request) – Odpověď (Response).
- **Třívrstvá architektura:** Prezenční (vzhled), Logická (výpočty), Datová (úložiště).
- **Technologie:** HTML/CSS/JS (klient) vs. PHP/SQL (server a data).
- **HTTP:** Protokol, po kterém tato komunikace probíhá.