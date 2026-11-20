# Autority × Epico – prezentace (statický web pro Vercel)

Čistě statický web: `index.html` + složka `assets/` (videa, obrázky, loga). Žádný build ani framework.

## Nasazení – varianta A: Vercel CLI (nejrychlejší)

1. Nainstaluj Node.js (pokud ještě nemáš): https://nodejs.org
2. V terminálu přejdi do této složky:
   `cd autority-epico-prezentace`
3. Spusť:
   `npx vercel --prod`
4. Přihlas se (prohlížeč se otevře sám) a odpověz na otázky:
   - Set up and deploy? → **Y**
   - Which scope? → tým Autority (nebo tvůj účet)
   - Link to existing project? → **N**
   - Project name → např. `autority-epico`
   - In which directory is your code located? → **./**
   - Want to modify settings? → **N** (Vercel pozná statický web sám)
5. Po pár vteřinách dostaneš adresu typu `autority-epico.vercel.app`.

## Nasazení – varianta B: přes GitHub

1. Vytvoř nový repozitář a nahraj do něj obsah této složky.
2. Na https://vercel.com/new zvol **Import Git Repository**, vyber repozitář.
3. Framework Preset: **Other**, Build Command: prázdné, Output Directory: prázdné → **Deploy**.
4. Každý další push do repozitáře se nasadí automaticky.

## Vlastní doména (např. prezentace.autority.cz)

1. Ve Vercelu: projekt → **Settings → Domains** → zadej `prezentace.autority.cz` → **Add**.
2. Vercel ukáže CNAME záznam (typicky hodnota `cname.vercel-dns.com`, použij ale přesně tu, kterou ti zobrazí).
3. Ve Wixu: **Domains** → u domény autority.cz **Domain Actions → Manage DNS Records** → sekce **CNAME (Aliases)** → **+ Add Record**:
   - Host name: `prezentace`
   - Value: hodnota z Vercelu
4. Ulož. Ve Vercelu se doména během minut (max. 48 h) přepne na „Valid Configuration" a HTTPS se nastaví automaticky.

Pozn.: Pokud je doména k Wixu připojená přes *pointing* (ne přes name servery Wixu), přidej CNAME u registrátora domény, ne ve Wixu.

## Co je nastavené

- `noindex` – prezentace se nezobrazí ve vyhledávačích (je to klientský pitch). Pokud ji chceš veřejně indexovat, smaž meta tag `robots` v `index.html` a hlavičku `X-Robots-Tag` ve `vercel.json`.
- Assety se cachují 24 h. Když vyměníš video pod stejným názvem, může se návštěvníkům den zobrazovat stará verze – nejjednodušší je nový soubor pojmenovat jinak.
- Odkazy na konkrétní slide: `…/#s5`.

## Úpravy

Texty jsou přímo v `index.html` (každý slide je `<section id="s1">` … `<section id="s9">`). Po úpravě stačí znovu `npx vercel --prod`.
