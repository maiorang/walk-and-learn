# Walk and Learn — deploy su GitHub Pages

Questa cartella è **pronta da pubblicare**. Contiene i 12 MP3, il feed `podcast.xml`,
la `cover.jpg`, una pagina `index.html` e `.nojekyll`.

URL finali previsti (utente `gmaiorano`, repo `walk-and-learn`):
- Pagina:  `https://gmaiorano.github.io/walk-and-learn/`
- **Feed podcast:** `https://gmaiorano.github.io/walk-and-learn/podcast.xml`

> ⚠️ Se cambi utente o nome repo, gli URL dentro `podcast.xml` e `index.html` non combaciano più:
> rigenerali con `genera_feed_rss.py --base-url https://<utente>.github.io/<repo>/`.

## Opzione A — da web (zero git, ~3 min)
1. Vai su https://github.com/new → **Repository name:** `walk-and-learn` → **Public** → *Create*.
2. Nel repo: **Add file → Upload files** → trascina **tutto** il contenuto di questa cartella
   (i 12 `.mp3`, `podcast.xml`, `cover.jpg`, `index.html`, `.nojekyll`) → *Commit changes*.
3. **Settings → Pages** → *Source:* `Deploy from a branch` → *Branch:* `main` / `/ (root)` → *Save*.
4. Dopo 1-2 minuti il sito è online. Apri `https://gmaiorano.github.io/walk-and-learn/` per controllare.

## Opzione B — da terminale (git)
```bash
cd "<questa cartella>"
git init && git add -A && git commit -m "Walk and Learn — Claude Code 101"
git branch -M main
git remote add origin https://github.com/gmaiorano/walk-and-learn.git
git push -u origin main
```
Poi abilita **Settings → Pages** come al punto 3 dell'opzione A.

## Aggiungere il feed all'app podcast
Copia `https://gmaiorano.github.io/walk-and-learn/podcast.xml` e:
- **Apple Podcasts (Mac):** Archivio → menu *File* → "Aggiungi un programma via URL…" → incolla.
  *(Su iPhone non c'è l'opzione: aggiungilo dal Mac, si sincronizza con lo stesso Apple ID;
  oppure usa Overcast/Pocket Casts che accettano l'URL direttamente sul telefono.)*
- **Overcast:** `+` → *Add URL* → incolla.
- **Pocket Casts:** *Cerca* → incolla l'URL del feed.

La velocità (1×–2×) si regola nell'app; il tono resta naturale. Le pause sono già nell'audio.

## Note
- Dimensione totale ≈ 70 MB: dentro i limiti di GitHub Pages (file max 100 MB, repo < 1 GB).
- GitHub Pages serve gli `.mp3` come `audio/mpeg` e supporta il seek (range requests).
- Le durate nel feed sono calcolate dalla dimensione (CBR 128 kbps): i file MP3 sono concatenati
  da più blocchi e `afinfo`/alcuni player leggono male la durata interna — la riproduzione è
  comunque completa. Con `ffmpeg` installato si potrebbero riscrivere gli header per durata esatta.
