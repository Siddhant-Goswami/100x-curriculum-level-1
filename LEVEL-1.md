# Level 1 fork of 100x-curriculum

This repo is the content behind the self-paced **Apply AI Level 1** app (`Siddhant-Goswami/100x-level-1`, where it is the `100x-curriculum` submodule). It is the upstream curriculum, `Siddhant-Goswami/100x-curriculum`, with Level 1's own edits on top.

## How it stays in sync

- **Upstream to this fork.** `.github/workflows/sync-upstream.yml` runs every 30 minutes (and from the Actions tab) and merges upstream `main` into `main`.
  - Pages Level 1 has rewritten are listed in `.gitattributes` with `merge=ours`. The sync keeps the Level 1 version, and if upstream changed one of them it opens an issue linking the upstream diff, so someone decides what to carry over.
  - Any other conflict stops the sync and opens a pull request from the `sync/upstream` branch. Resolve it and merge; the next run carries on.
- **This fork to the app.** A workflow in the Level 1 app repo checks this fork every two hours, checks that every page the app links to still exists, and moves the submodule forward. The app then redeploys.

Upstream is never written to from here. To change the shared curriculum, change it upstream and let it flow down.

## What Level 1 changes

| Edit | Where | Why |
|---|---|---|
| Lessons split into parts | `<!-- level-1 part: Title -->` before the first `<section>` of each part, in the notes pages | A beginner reads one 6 to 13 minute part at a time, with a stopping point between parts. Comments only, so the pages look the same here and upstream, and merges stay clean. |
| Idea to App notes | `c8/module-2/what-to-build/idea-to-app-notes.html` | Rewritten for Level 1 around the North Star standard (owned: `merge=ours`) |
| Assignment 1 brief | `c8/module-2/what-to-build/assignment-1.html` | The Level 1 brief; the app cites its rules word for word (owned: `merge=ours`) |

## Editing

- **Part markers.** A part starts at the marker and runs to the next one. Markers must sit directly before a `<section id="sNN">`; the app's sync step fails the build if one does not. Split a lesson only when its reading runs past about 12 minutes, and break where the argument turns, not at a word count. A lesson with no markers is one part.
- **A Level 1 rewrite of another page.** Edit the page here and add its path to `.gitattributes` with `merge=ours`.
- **Small Level 1 tweaks to a shared page.** Edit it here without listing it. Upstream changes merge in around the edit, and a clash opens a pull request.
