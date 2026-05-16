# 27. JavaScriptové knihovny a pluginy

---

### 1. Význam a rozdíl mezi knihovnou a pluginem

Ve vývoji webových aplikací se málokdy píše veškerý kód znovu. Používají se k tomu již připravené balíčky kódu.

- **JavaScriptová knihovna:** Rozsáhlý soubor funkcí a nástrojů, které zjednodušují složité úkoly (např. manipulaci s DOM, animace nebo komunikaci se serverem). Knihovna ti dává nástroje, které sám voláš.
- **Plugin:** Menší, úzce zaměřený skript, který obvykle vyžaduje nějakou knihovnu (často jQuery) ke svému běhu. Plugin řeší jeden konkrétní problém, například galerii obrázků nebo kalendář.

---

### 2. Výhody, nevýhody a způsoby připojení

Použití hotového kódu má své pro i proti, které je u maturity dobré zmínit.

| **Výhody** | **Nevýhody** |
| --- | --- |
| **Rychlost vývoje:** Nemusíš programovat složité věci od začátku.   | **Velikost souborů:** Knihovny mohou zpomalit načítání webu.   |
| **Kompatibilita:** Knihovny řeší rozdíly mezi prohlížeči za tebe.   | **Závislost:** Pokud knihovna přestane fungovat, může se rozbít celý web.   |

**Možnosti připojení:**

1. **Lokální soubor:** Knihovnu stáhneš a uložíš na svůj server. Funguje i bez internetu, ale musíš se starat o aktualizace.
2. **CDN (Content Delivery Network):** Skript připojíš pomocí odkazu na vzdálený server (např. Google CDN).
    - *Výhoda:* Pokud uživatel navštívil jiný web se stejnou knihovnou, prohlížeč ji má v mezipaměti (cache) a nemusí ji stahovat znovu.

---

### 3. Knihovna jQuery

I když jsou dnes populární moderní frameworky (jako React), jQuery je stále „maturitní klasikou“ díky své jednoduchosti.

- **Hlavní myšlenka:** "Write less, do more" (Piš méně, dělej více).
- **Základní syntaxe:** Využívá znak **`$`** jako zkratku pro funkci jQuery.
- **Struktura:** `$(selektor).akce()`.
    - `selektor` najde HTML prvek (stejně jako v CSS).
    - `akce` s prvkem něco provede.

---

### 4. Příklady pluginů

Pluginy rozšiřují základní funkčnost. U maturity stačí uvést typické příklady:

- **Lightbox / PhotoSwipe:** Pro efektní zobrazování obrázků v překryvné vrstvě.
- **Slick / Owl Carousel:** Pro tvorbu posuvných bannerů (sliderů).
- **Select2:** Pro vylepšené a vyhledávací rozbalovací seznamy.

---

### Praktický příklad: Porovnání JS a jQuery

Zde uvidíš, jak jQuery zjednodušuje kód pro skrytí prvku po kliknutí:

JavaScript

```jsx
// Klasický JavaScript
document.getElementById("tlacitko").addEventListener("click", function() {
    document.getElementById("text").style.display = "none";
});

// jQuery (mnohem kratší a čitelnější)
$("#tlacitko").click(function() {
    $("#text").hide(); // Funkce hide() je vestavěná v jQuery
});
```

---

### 💡 Tahák pro maturanta (klíčové body):

- **Knihovna** (např. jQuery) je balík nástrojů, **plugin** je konkrétní doplněk (např. galerie) .
- **CDN** je nejčastější způsob připojení – je rychlé a efektivní.
- **jQuery syntaxe:** Vždy začíná dolarem `$(...)` a používá CSS selektory.
- **Základní funkce jQuery:** `hide()`, `show()`, `toggle()`, `addClass()`, `ajax()`.
- Při použití pluginu nezapomeň, že v HTML musíš nejdříve připojit **knihovnu** a až potom samotný **plugin**.