# ClipCut.cz

Jednoduchá **statická** webová stránka pro [ClipCut.cz](https://clipcut.cz) — střih reels a videí. Není tu žádný build, React ani databáze: jeden soubor `index.html`, obrázky, videa a styly přes CDN (Tailwind, ikony Lucide, fonty Google).

Tento návod je psaný pro **úplné začátečníky** — stačí prohlížeč a pár příkazů v terminálu.

---

## Co budete potřebovat

| Nástroj | K čemu | Kde stáhnout |
|--------|--------|--------------|
| **Git** | Stažení a odesílání změn na GitHub | [git-scm.com](https://git-scm.com/) |
| **Prohlížeč** | Kontrola, jak web vypadá | Chrome, Firefox, Safari… |
| **Terminál** | Spuštění lokálního serveru | Na Macu: *Terminal*, na Windows: *PowerShell* nebo *Git Bash* |

**Nepotřebujete** Node.js, npm ani žádnou instalaci závislostí — web se „neskládá“, jen se otevře přes HTTP server.

---

## 1. Stažení projektu z GitHubu

V terminálu zadejte (složku si můžete změnit):

```bash
cd ~/Sites
git clone https://github.com/machal/clipcut-cz.git
cd clipcut-cz
```

Máte-li projekt už naklonovaný, stačí v jeho složce:

```bash
git pull
```

---

## 2. Spuštění webu na počítači

Web **nepouštějte** dvojklikem na `index.html` (`file://…`). U videí a některých věcí v prohlížeči to často nefunguje správně. Použijte **lokální server** — v adresní řádce pak uvidíte `http://localhost:…`.

### Varianta A: Python (nejjednodušší, Mac i Windows)

Python 3 bývá na Macu už nainstalovaný. Ve složce projektu:

```bash
python3 -m http.server 8080
```

V prohlížeči otevřete: **http://localhost:8080**

Server ukončíte v terminálu klávesami **Ctrl + C**.

### Varianta B: Node (pokud máte nainstalovaný Node.js)

```bash
npx --yes serve -p 8080
```

Pak opět **http://localhost:8080**.

---

## 3. Co v repozitáři je

```
clipcut-cz/
├── index.html          # celá stránka (texty, sekce, styly v <style>)
├── clipcut-logo.jpg    # logo a náhled při sdílení
├── honza.jpg           # fotka v sekci O nás
├── krystof.jpg
├── ukazka-1.mp4        # ukázky v portfoliu
├── ukazka-2.mp4
├── frontkec-reel.mp4
├── ukazka-3.mp4        # v repu je, v HTML se nemusí používat
└── README.md           # tento soubor
```

**Úpravy textů a cen:** otevřete `index.html` v editoru (Cursor, VS Code, cokoli) a hledejte sekce podle komentářů, např. `<!-- Ceník Section -->`, `<!-- Footer -->`.

**Barvy a vzhled:** většina stylů je v `<style>` na začátku souboru; layout používá [Tailwind CSS](https://tailwindcss.com/) z CDN (třídy jako `text-gray-400`, `glass-strong`).

---

## 4. Jak uložit změny na GitHub (stručně)

Ve složce projektu:

```bash
git status                    # co se změnilo
git add index.html            # přidat konkrétní soubor, nebo: git add .
git commit -m "Upravil jsem text v patičce"
git push
```

Commit a push děláte jen když chcete změny sdílet na GitHubu. Lokální náhled v prohlížeči **push nevyžaduje**.

---

## 5. Nasazení na internet (orientačně)

Web je jen statické soubory — stačí je **nahostovat** někde, kde běží obyčejný web server:

- vlastní doména + hosting (FTP / panel u poskytovatele),
- [GitHub Pages](https://pages.github.com/) (pro jednoduchý web z repa),
- [Netlify](https://www.netlify.com/), [Cloudflare Pages](https://pages.cloudflare.com/) a podobně.

Na produkci musí být na adrese (např. `https://clipcut.cz/`) dostupné **všechny** soubory z repa včetně `.mp4` a `.jpg` — cesty v HTML jsou relativní (`src="ukazka-1.mp4"`).

> **Poznámka:** videa jsou velká (řádově desítky MB). První `git clone` může trvat déle; na GitHubu je limit **100 MB na jeden soubor**.

---

## 6. Časté problémy

| Problém | Řešení |
|--------|--------|
| Videa se nepřehrávají | Spouštějte web přes `http://localhost`, ne přes `file://` |
| Po úpravě nevidím změnu | Obnovte stránku (Ctrl+R / Cmd+R), případně tvrdý refresh (Ctrl+Shift+R) |
| Port 8080 je obsazený | Zkuste jiný port: `python3 -m http.server 3000` → http://localhost:3000 |
| `git push` selže | Musíte být přihlášeni k GitHubu a mít práva do repa `machal/clipcut-cz` |

---

## Odkazy

- **Živý web:** https://clipcut.cz  
- **Repozitář:** https://github.com/machal/clipcut-cz  

Máte-li dotaz k obsahu nebo cenám na webu, pište přes kontakt na stránce — technické úpravy řeší správce repozitáře.
