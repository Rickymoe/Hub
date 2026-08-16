# Hub — oversiktsside Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Bygg en enkel, privat statisk side som lister alle Rickys 19 live nettsider gruppert etter kategori, som erstatning for nettleser-favoritter.

**Architecture:** Én statisk HTML-side (`index.html` + `css/style.css`), ingen backend, ingen build-steg. Hostet som privat GitHub-repo med GitHub Pages — GitHub Pro-abonnementet gir automatisk tilgangsbegrensning til kun innloggede brukere med repo-tilgang (kun Ricky), så ingen egen autentisering trengs.

**Tech Stack:** Ren HTML/CSS, GitHub Pages (privat repo).

**Spec:** Ingen egen spec-fil — design avtalt direkte i chat under brainstorming-sesjon 2026-08-16 (kategorisering, "bare navn + lenke"-innhold, privat repo bekreftet av bruker).

## Global Constraints

- Repoet MÅ være privat (bruker har eksplisitt bedt om dette siden siden lenker til private prosjekter).
- Ingen backend/autentiseringskode — tilgangsbegrensning skjer utelukkende via GitHub Pages' private-repo-støtte (GitHub Pro).
- Kun navn + lenke per prosjekt — ingen beskrivelser eller skjermbilder (bekreftet av bruker).
- Kategorier og rekkefølge: X-serien, Formidling, Simulatorer & verktøy, Redesign for andre, Eget merkevarebygging.

---

### Task 1: Bygg og test oversiktssiden lokalt

**Files:**
- Create: `index.html`
- Create: `css/style.css`

**Interfaces:**
- Produces: en fullstendig, ferdig statisk side. Ingen avhengigheter fra andre tasks.

- [ ] **Step 1: Opprett `index.html`**

```html
<!DOCTYPE html>
<html lang="no">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Hub</title>
<link rel="stylesheet" href="css/style.css">
</head>
<body>
<main>
  <h1>Hub</h1>
  <p class="sub">Oversikt over alle live nettsider.</p>

  <section>
    <h2>X-serien</h2>
    <ul class="links">
      <li><a href="https://rickymoe.github.io/X1/" target="_blank" rel="noopener">X1</a></li>
      <li><a href="https://rickymoe.github.io/X2/" target="_blank" rel="noopener">X2</a></li>
      <li><a href="https://rickymoe.github.io/X3/" target="_blank" rel="noopener">X3</a></li>
      <li><a href="https://rickymoe.github.io/X4/" target="_blank" rel="noopener">X4</a></li>
      <li><a href="https://rickymoe.github.io/X5/" target="_blank" rel="noopener">X5</a></li>
    </ul>
  </section>

  <section>
    <h2>Formidling</h2>
    <ul class="links">
      <li><a href="https://rickymoe.github.io/Y1/" target="_blank" rel="noopener">Y1</a></li>
    </ul>
  </section>

  <section>
    <h2>Simulatorer &amp; verkt&oslash;y</h2>
    <ul class="links">
      <li><a href="https://rickymoe.github.io/globe/" target="_blank" rel="noopener">Globus</a></li>
      <li><a href="https://rickymoe.github.io/sola/" target="_blank" rel="noopener">Sola</a></li>
      <li><a href="https://rickymoe.github.io/Sol/" target="_blank" rel="noopener">Sol</a></li>
      <li><a href="https://rickymoe.github.io/reisevei/" target="_blank" rel="noopener">Reisevei</a></li>
    </ul>
  </section>

  <section>
    <h2>Redesign for andre</h2>
    <ul class="links">
      <li><a href="https://rickymoe.github.io/MonteHolmis/" target="_blank" rel="noopener">MonteHolmis</a></li>
      <li><a href="https://rickymoe.github.io/kuvaas/" target="_blank" rel="noopener">Kuvaas</a></li>
      <li><a href="https://rickymoe.github.io/HUT/" target="_blank" rel="noopener">HUT</a></li>
      <li><a href="https://rickymoe.github.io/StokkeRegnskap/" target="_blank" rel="noopener">StokkeRegnskap</a></li>
      <li><a href="https://rickymoe.github.io/UniEmb/" target="_blank" rel="noopener">UniEmb</a></li>
      <li><a href="https://rickymoe.github.io/mokollen/" target="_blank" rel="noopener">Mokollen</a></li>
      <li><a href="https://rickymoe.github.io/helena-film/" target="_blank" rel="noopener">Helena</a></li>
    </ul>
  </section>

  <section>
    <h2>Eget merkevarebygging</h2>
    <ul class="links">
      <li><a href="https://rickymoe.github.io/rickys-webdesign/" target="_blank" rel="noopener">Webdesign by Ricky</a></li>
      <li><a href="https://rickymoe.github.io/FilmProsjektet/" target="_blank" rel="noopener">FilmProsjekter</a></li>
    </ul>
  </section>
</main>
</body>
</html>
```

- [ ] **Step 2: Opprett `css/style.css`**

```css
:root {
  --bg: #0a0a0c;
  --text: #e8e8ea;
  --muted: #8a8a90;
  --accent: #c9a84c;
}

* { box-sizing: border-box; }

body {
  margin: 0;
  background: var(--bg);
  color: var(--text);
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
  padding: 48px 24px;
}

main {
  max-width: 640px;
  margin: 0 auto;
}

h1 {
  font-size: 28px;
  margin: 0 0 4px;
}

.sub {
  color: var(--muted);
  margin: 0 0 40px;
  font-size: 14px;
}

section {
  margin-bottom: 32px;
}

h2 {
  font-size: 12px;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--muted);
  margin: 0 0 12px;
  border-bottom: 1px solid rgba(255,255,255,0.1);
  padding-bottom: 8px;
}

.links {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.links li a {
  display: inline-block;
  color: var(--text);
  text-decoration: none;
  padding: 8px 14px;
  border: 1px solid rgba(255,255,255,0.14);
  border-radius: 6px;
  font-size: 14px;
  transition: border-color 0.15s, color 0.15s;
}

.links li a:hover {
  border-color: var(--accent);
  color: var(--accent);
}
```

- [ ] **Step 3: Verifiser antall lenker**

Run: `grep -o '<a href' index.html | wc -l`
Expected: `19`

- [ ] **Step 4: Start lokal server og verifiser at siden laster**

Run:
```bash
python3 -m http.server 8020 &
sleep 1
curl -s -o /dev/null -w "%{http_code}\n" http://localhost:8020/index.html
kill %1
```
Expected: `200`

- [ ] **Step 5: Commit**

```bash
git add index.html css/style.css
git commit -m "Legg til Hub-oversiktsside med alle live prosjekter"
```

---

### Task 2: Publiser som privat GitHub Pages-side

**Files:**
- Ingen nye filer — kun repo-oppsett og deploy.

**Interfaces:**
- Consumes: `index.html` og `css/style.css` fra Task 1 (må være committet).

- [ ] **Step 1: Opprett privat GitHub-repo og push**

```bash
cd ~/Dokumenter/Koding/Hub
gh repo create Rickymoe/Hub --private --source=. --remote=origin --push
```

Expected: kommandoen skriver ut URL-en til det nyopprettede private repoet, og `git remote -v` viser `origin` pekende mot `git@github.com:Rickymoe/Hub.git`.

- [ ] **Step 2: Skru på GitHub Pages fra `master`-branchen, rot-mappe**

```bash
gh api repos/Rickymoe/Hub/pages -X POST -f "source[branch]=master" -f "source[path]=/"
```

Expected: JSON-svar med `"status":"building"` eller `"html_url":"https://rickymoe.github.io/Hub/"`.

- [ ] **Step 3: Vent til bygg er ferdig og verifiser at siden er tilgangsbegrenset**

Run:
```bash
sleep 30
gh api repos/Rickymoe/Hub/pages/builds/latest --jq '.status'
curl -sI https://rickymoe.github.io/Hub/ | head -1
```
Expected: build-status er `built`, og curl (uten innlogging) returnerer IKKE `200 OK` — enten en redirect til GitHub-innlogging eller et ikke-200-svar, som bekrefter at siden er beskyttet av GitHub Pro sin private-Pages-tilgangskontroll.

- [ ] **Step 4: Be Ricky bekrefte tilgang i egen nettleser**

Ikke en kommando — informer Ricky om at han må åpne `https://rickymoe.github.io/Hub/` i sin egen innloggede nettleser og bekrefte at siden laster og alle 19 lenker fungerer.
