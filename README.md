# Kituu Junior School — CBC Results Portal

This is your real Sision Junior School app, adapted for Kituu Junior School
(Samburu) with **single-stream classes only** — Grade 7, 8, and 9, no East/West
split anywhere, ever. Every other feature is untouched: CBC 8-band grading
(EE1/EE2/ME1/ME2/AE1/AE2/BE1/BE2), pathway performance profiles, class ranking,
subject means, term-to-term comparison, printable/downloadable report forms,
CSV import/export, and the Year Advancement Wizard for promoting learners.

## Files
- `index.html` — the whole app
- `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png` — makes it installable as a home-screen app (PWA)
- `db.json` — empty starting database (learners get registered by you)

## Upload to GitHub Pages
1. Create a new **public** repo, e.g. `Kituu-Junior`.
2. Upload all five files (`index.html`, `manifest.json`, `sw.js`, `icon-192.png`,
   `icon-512.png`) plus `db.json` to the repo root, on the `main` branch.
3. Settings → Pages → Deploy from branch → `main` / `root`. Your site will be at
   `https://<your-username>.github.io/<repo-name>/`.

## Excel & Results Analysis (new)
- **⬇ Excel (Filled)** and **⬇ Excel (Blank Template)** — genuine `.xlsx` files
  (not just CSV) with the same columns as before, formatted with sensible
  column widths.
- **📥 Import Marks (Excel)** — bring a filled `.xlsx` template back in,
  matching by learner name (case-insensitive), same as the CSV import.
- **📊 Results Analysis** button — overall EE/ME/AE/BE distribution, class
  mean, pass rate (ME and above), per-subject grade distribution and means,
  and a Top 5 performers table. Opens as an overlay on the results screen.
- CSV export/import is still there too — Excel is additional, not a replacement.

## School Settings & Manage Classes (new)
Two new buttons appear in the header for admin only:
- **🏫 School Settings** — edit the school name, county, and motto. This shows up
  on the login screen, report cards, and class lists immediately after saving.
- **🏫 Manage Classes** — add, rename, or remove classes per grade. You're no
  longer limited to one class or exactly two (East/West) — add as many named
  classes as you actually have, e.g. Grade 7 "Ruby", "Emerald", "Topaz".
  Ranking automatically works per class and combined across the whole grade.
  Removing a class doesn't delete its saved data from GitHub — it just stops
  showing in the app. Merging two classes into one isn't built yet; if you need
  that, add the destination class, manually move learners over one at a time
  via **Edit Learner**, then remove the empty one.

## First-time setup
1. Open the site. You'll see a **Database Settings** screen first — this connects
   the app to your GitHub repo so everyone's data is shared. Enter:
   - **Owner**: your GitHub username
   - **Repo**: your repo name
   - **Token**: a GitHub Personal Access Token with `repo` scope
     (GitHub → Settings → Developer settings → Personal access tokens → generate one,
     scope: `repo`)
2. Once connected, you'll get a **teacher link** with the token embedded — this is
   what makes it a one-tap login for teachers on their own phones (no typing
   owner/repo/token). **Only share this link with staff you trust**, and treat it
   like a password — anyone with the token link can write to your repo.
3. Log in as admin: username `admin`, password `adminkituu2026`.
   **Change this immediately** — go to **✏️ Manage Team** and update the admin
   entry's password.

## Logins to give your staff
Every subject account below covers **Grade 7, 8, and 9** — one login per subject,
not per grade.

| Login | Username | Password |
|---|---|---|
| Admin | `admin` | `adminkituu2026` |
| Mathematics | `Mathematics` | `math2026` |
| English | `English` | `eng2026` |
| Kiswahili | `Kiswahili` | `kis2026` |
| Integrated Science | `Science` | `sci2026` |
| Pre-Technical Studies | `PreTechnical` | `pts2026` |
| Agriculture & Nutrition | `Agriculture` | `2026agric` |
| Social Studies | `SocialStudies` | `ss2026` |
| CRE | `CRE` | `cre2026` |
| Creative Arts & Sports | `CreativeArts` | `cas2026` |

**Class Teachers** aren't pre-filled (they're tied to a specific person, not a
fixed subject) — three placeholder accounts are ready for you to personalize:

| Login | Grade | Default password |
|---|---|---|
| `classteacher7` | Grade 7 | `2026` |
| `classteacher8` | Grade 8 | `2026` |
| `classteacher9` | Grade 9 | `2026` |

Go to **✏️ Manage Team** as admin to rename each account and set real passwords
for your actual teachers — every login's real name and password can be changed
from there without touching the code.

## Registering learners
As any class teacher or admin: open a class → **+ Learner** button on the
results screen. Names can also be added in bulk during the **Year Advancement
Wizard** when registering a new Grade 7 intake, or imported via the
**📥 Import Marks (CSV)** button once you've exported a blank template with
**⬇ Marks Template (CSV)**.

## What every role can do
- **Admin** — everything: connect/manage the database, manage every teacher's
  login, open any class, run the Year Advancement Wizard, all downloads/prints.
- **Class Teacher** — opens only their assigned grade: register/edit learners,
  enter marks for all subjects if needed, add class comments, print/download
  class lists and report cards, CSV import/export.
- **Subject Teacher** — opens any of Grade 7/8/9 for their one subject: enters
  marks, sees grade distribution, prints/downloads for that subject's data.

## Download & print buttons (all confirmed working)
- ⬇ Download Blank Class List / 🖨 Print Blank Class List
- ⬇ Download Results List / 🖨 Print Results List (once marks exist)
- ⬇ Download All Report Forms / 🖨 Print All Report Forms
- ⬇ CSV (full marks export)
- ⬇ Marks Template (CSV) — blank template to fill offline
- 📥 Import Marks (CSV) — bring filled-in marks back in

## Year Advancement Wizard
Appears automatically for admins from 2027 onward (or trigger manually via
**🔄 Re-run Year Setup**) to promote Grade 9 out, move Grade 8 → 9, Grade 7 → 8,
and register a new Grade 7 intake — all as single classes, since Kituu has no
stream splitting anywhere.

## Notes
- Data is stored in `db.json` in your GitHub repo via the GitHub API — every
  teacher's device stays in sync automatically as long as they're connected.
- Report cards and class lists print via the browser's Print dialog
  (Print → Save as PDF).
- Never share your GitHub Personal Access Token outside the app's own
  "Database Settings" screen — not in chat, not in a public link.
- Fixed in this build: subject-teacher logins (e.g. Mathematics, English, etc.)
  were crashing to a blank white screen right after logging in. The bug was
  in how those accounts' "can access every class" setting got read after the
  Manage Classes rework — fixed, and confirmed subject-teacher login now
  works end to end. If you still see a blank screen, it's almost certainly
  the cached old version — clear site data once or check in a private tab.
- Fixed in this build: the "Marks Template (CSV)" and "CSV" download buttons
  had a bug that would have made them fail — that's resolved now.
- The Year Advancement Wizard now carries each class forward by name (e.g.
  "Grade 8 Ruby" → "Grade 9 Ruby") instead of assuming East/West — matches
  Manage Classes. Merging two classes into one during promotion still isn't
  built; if you need it, promote as-is then use Manage Classes/Edit Learner
  afterward to consolidate.

## Is this file specific to Kituu?

Mostly no, but not entirely — here's the honest breakdown:

**Fully generic, controlled by School Settings:**
- School name, county, motto — shown on login, report cards, class lists, and
  the browser tab title, all update live once saved
- Every login, class, and grading band — all editable, nothing Kituu-specific baked in

**Still hardcoded (can't be changed without editing the file):**
- `apple-mobile-web-app-title` in the HTML `<head>` — the name used when
  someone "Adds to Home Screen." This is read once at install time by the
  phone's OS, so it can't be changed by the app itself at runtime.
- `manifest.json`'s `name`/`short_name` — same limitation, it's a separate
  static file read by the browser before your app's JS even runs.
- The default admin password (`adminkituu2026`) has "kituu" baked into the
  string itself — works fine for any school, but worth changing anyway.

**Practical constraint, not a code limitation:**
- One GitHub repo = one school's data. Reusing this for a second school means
  a separate repo, separate GitHub Pages deployment, and its own School
  Settings — not just changing a name field.

If you want a second school fully set up (its own repo-ready files, its own
default logins), tell me and I'll generate a clean copy rather than you
hand-editing this one.
