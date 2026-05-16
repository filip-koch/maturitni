# 16. Služba WWW, jazyk HTML

---

### 1. Internet a služba WWW

U maturity začni rozlišením mezi Internetem a WWW, což jsou pojmy, které se často pletou:

- **Internet:** Globální systém propojených počítačových sítí. Mezi jeho služby patří například e-mail, FTP nebo právě WWW.
- **Služba WWW (World Wide Web):** Vznikla v CERNu (Tim Berners-Lee) jako systém propojených hypertextových dokumentů.
- **Základní pojmy:**
    - **Webový server:** Počítač/software, který ukládá a poskytuje webové stránky.
    - **Webový prohlížeč:** Klient (např. Chrome, Firefox), který interpretuje kód (HTML, CSS) a zobrazuje ho uživateli.
    - **HTTP/HTTPS:** Protokol pro přenos dat mezi serverem a prohlížečem.
    - **URL:** Jednotná adresa zdroje na internetu.

### 2. Webové standardy a W3C

Web by nefungoval bez pravidel, která zajišťují, že se stránka zobrazí všude stejně:

- **Konsorcium W3C:** Mezinárodní organizace, která vyvíjí webové standardy.
- **Hlavní standardy:** HTML (struktura), CSS (vzhled) a JavaScript (chování).
- **Formáty médií:** Standardy určují i podporované formáty obrázků (JPEG, PNG, SVG), audia a videa.

---

### 3. Jazyk HTML – Význam a syntaxe

HTML (**HyperText Markup Language**) není programovací, ale **značkovací jazyk**.

- **Syntaxe:** Využívá značky (tagy) uzavřené v lomených závorkách (např. `<p>` pro odstavec).
- **Verze:** Aktuální standard je **HTML5**, který přinesl sémantické značky a lepší podporu multimédií.
- **Základní struktura:** Každý dokument musí obsahovat deklaraci typu (`<!DOCTYPE html>`), kořenový prvek `<html>`, hlavičku `<head>` (metadata, znaková sada UTF-8) a tělo `<body>` (viditelný obsah).

---

### 4. Strukturování obsahu a HTML5

Pro moderní web je klíčová **sémantika** (význam prvků):

- **Bloková struktura:** Rozděluje stránku na logické části.
    - **Obecné:** `<div>` (univerzální blok), `<span>` (řádkový prvek).
    - **HTML5 sémantika:** `<header>` (záhlaví), `<nav>` (navigace), `<main>` (hlavní obsah), `<article>` (článek), `<footer>` (patička).
- **Textové prvky:** Nadpisy `<h1>` až `<h6>`, odstavce `<p>`, seznamy (`<ul>`, `<li>`), tabulky `<table>` a zvýraznění (`<strong>`, `<em>`).

---

### 5. Odkazy, média a entity

- **Odkazy:** Značka `<a>` s atributem `href` (cíl odkazu). Rozlišujeme odkazy absolutní (celá URL), relativní (v rámci webu) nebo kotvy (na stejnou stránku).
- **Média:**
    - `<img>`: Obrázky (vyžaduje atributy `src` a `alt` pro přístupnost).
    - `<video>` a `<audio>`: Vkládání multimédií bez nutnosti pluginů.
- **Entity:** Speciální sekvence začínající `&` pro zobrazení znaků, které mají v HTML jiný význam (např. `&lt;` pro `<`) nebo pro pevnou mezeru `&nbsp;`.

---

### 6. Validace

Validace je proces kontroly, zda je kód napsán podle pravidel W3C. Pomáhá odhalit chyby (např. neuzavřené tagy), což zajišťuje správné zobrazení v prohlížečích a lepší výsledky ve vyhledávačích (SEO).

---

### Praktický příklad: Základní struktura dokumentu

HTML

```html
<!DOCTYPE html>
<html lang="cs">
<head>
    <meta charset="UTF-8"> <title>Maturitní otázka 16</title>
</head>
<body>
    <header>
        <h1>Vítejte na mém webu</h1>
    </header>
    
    <main>
        <p>Toto je ukázka <strong>sémantického</strong> HTML5.</p>
        <img src="obrazek.jpg" alt="Popis obrázku pro nevidomé">
        <a href="https://www.w3.org">Odkaz na W3C</a>
    </main>

    <footer>
        <p>&copy; 2026 Maturant</p>
    </footer>
</body>
</html>
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Internet vs. WWW:** Internet je síť, WWW je služba v této síti.
- **W3C:** Autorita určující standardy (HTML, CSS).
- **HTML5:** Klade důraz na sémantiku (`<header>`, `<main>`, `<nav>`).
- **Povinné prvky:** `DOCTYPE`, `html`, `head` (meta charset), `body`.
- **Odkazy a obrázky:** Klíčové atributy jsou `href` (pro odkaz) a `src` + `alt` (pro obrázek).
- **Validace:** Kontrola správnosti kódu pomocí nástrojů W3C.