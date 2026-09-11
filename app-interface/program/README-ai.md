# Baza de cunoștințe „Program" — note pentru cine o publică

Conținutul acestui folder este documentație publică în limba română despre modulul de programare (Program) din TEAMM.
Este scris pentru două categorii de cititori: personalul centrelor și asistenții AI (ChatGPT, Claude, Gemini) pe care
personalul îi întreabă „cum fac X?".

## Publicare

1. Copiază folderul `app-interface/program/` în repo-ul care alimentează help.teamm.work.
2. Adaugă grupul din `_navigation.json` în `docs.json` (tab-ul App Interface). Ordinea paginilor este ordinea de citire.
3. Nu adăuga `onboarding/schedule.mdx` (walkthrough Scribe din 2024, fluxul vechi) în navigație.
4. Opțional, în `docs.json`, activează meniul contextual pe pagini: `"contextual": { "options": ["copy", "view", "chatgpt", "claude", "mcp"] }`
   (verifică numele opțiunilor în documentația Mintlify curentă).
5. După deploy verifică:
   - `https://help.teamm.work/llms.txt` listează paginile noi;
   - `https://help.teamm.work/app-interface/program/sejur/pasul-4-oaspeti.md` returnează articolul;
   - `https://help.teamm.work/mcp` rămâne activ (răspunde 405 la GET).

## Convenții pentru pagini noi sau modificate

- Frontmatter `title` + `description` în română; `description` este ce vede asistentul AI în index.
- Prima linie: `**Unde în aplicație:** … (/admin/...)`.
- Secțiunea `## Întrebări la care răspunde pagina` este cârligul de regăsire: formulează întrebările așa cum le-ar pune personalul.
- Etichetele din interfață se citează exact, cu ghilimele românești „…".
- Fără capturi de ecran: se învechesc, iar asistenții AI citesc textul.
- Sursele textelor: fișierele `*.entity-info.ts`, `scheduling-config.tooltips.ts`, `schedule-verify.catalog.ts` / `.text.ts`
  și `schedule-flow.config.ts` din codul aplicației. Când se schimbă un text acolo, actualizează pagina corespunzătoare.

## Test de regăsire

În Claude sau ChatGPT: lipește adresa unei pagini și pune 3 întrebări din blocul „Întrebări la care răspunde pagina".
Apoi adaugă conectorul MCP `https://help.teamm.work/mcp` și pune aceleași întrebări fără adresă. Răspunsurile trebuie să
folosească etichetele din interfață și să trimită la pagina corectă.
