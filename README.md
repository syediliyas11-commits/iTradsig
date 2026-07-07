# Replacing WordPress with your iTradSig HTML site (cPanel)

**Goal:** itradsig.com stops showing WordPress and shows the black-green design
instead — same domain, same SSL, done from GoDaddy cPanel.

**Time:** ~15 minutes. **You need:** the `index.html` file I gave you.

> Follow the steps IN ORDER. Step 1 (backup) is your safety net — do not skip it.

---

## STEP 1 — Back up first (your undo button)

If anything goes sideways, this lets you put WordPress back exactly as it was.

1. Log into **GoDaddy → My Products → your hosting → Manage / cPanel Admin**.
2. In cPanel, find the **Files** section → click **Backup** (or **Backup Wizard**).
3. Click **Download a Full Account Backup** (or "Download a Home Directory Backup").
4. Save that file somewhere safe on your computer. Wait for it to finish.

> Optional extra safety: also use **Backup Wizard → Back up → MySQL Databases**
> to grab the WordPress database. Now you're fully covered.

---

## STEP 2 — Open the website folder

1. In cPanel → **Files** → **File Manager**.
2. In the left tree, click **public_html**.
   This is your website's root — everything here is what itradsig.com serves.
3. You'll see WordPress files here — things like:
   `wp-admin`, `wp-content`, `wp-includes`, `wp-config.php`, `index.php`, etc.

---

## STEP 3 — Clear WordPress out of the way

You want public_html to contain ONLY your new site. Two safe ways — pick one:

**Option A — Move WordPress into a backup folder (safest, reversible on the server)**
1. In File Manager, click **+ Folder** (top left), name it `old-wordpress`, Create.
2. Select ALL the WordPress files/folders in public_html
   (click the first, scroll down, Shift-click the last — or "Select All").
   *Do NOT select the new `old-wordpress` folder itself.*
3. Click **Move** (top toolbar), set the path to `/public_html/old-wordpress`, Move.
4. public_html is now empty except the `old-wordpress` folder. 

**Option B — Delete WordPress files (only if you're confident + backed up)**
1. Select all WordPress files/folders in public_html.
2. Click **Delete**. Confirm.
   (You have the Step 1 backup if you ever need them back.)

---

## STEP 4 — Upload your new site

1. Still in **public_html**, click **Upload** (top toolbar).
2. Drag your **`index.html`** onto the upload page (or Select File → choose it).
3. Wait for it to reach 100%, then go **Back to /public_html**.
4. Confirm `index.html` now sits directly inside public_html
   (NOT inside a subfolder — it must be at public_html/index.html).

---

## STEP 5 — Check it's live

1. Open a new browser tab → go to **https://itradsig.com**
2. You should see the black-green iTradSig site, with the padlock (SSL) intact.
3. If your browser still shows the old site, it may be cached:
   - Hard-refresh: **Ctrl+Shift+R** (Windows) or **Cmd+Shift+R** (Mac)
   - Or open the site in a private/incognito window.

Done — your domain now serves the design, exactly as built.

---

## If something's not right

**Still seeing WordPress / an old page**
- Make sure `index.html` is directly in public_html, not in a subfolder.
- Delete any leftover `index.php` in public_html (WordPress's index) — a stray
  `index.php` can take priority over `index.html`. Move it into `old-wordpress`.
- Hard-refresh / try incognito (caching).

**"Index of /" file listing instead of the site**
- The file is named wrong. It must be exactly **index.html** (lowercase).

**SSL / "not secure" warning**
- SSL is tied to the domain, so it should carry over. If it complains, in cPanel
  look for **SSL/TLS Status** and click **Run AutoSSL**, then wait a few minutes.

**Once everything works and you're happy**
- You can later delete the `old-wordpress` folder to free space — but keep your
  Step 1 backup on your computer regardless.

---

## Updating the site later

Any time you want to change the site (new prices, new copy):
1. Edit `index.html`
2. cPanel → File Manager → public_html → **Upload** → overwrite the old one.
That's the whole loop.

---

## Reminders about the site itself

- **Prices are already set** to $100 / $500 / $1500 in this file.
- **The numbers (win rate, ticker, equity) are examples** — make them real or keep
  them clearly illustrative before you promote the site widely.
- **This is the marketing site only.** The real auto-trading engine (your Phase 1
  repo) runs separately on a server when you connect it later.
- For a site advertising auto-trading of real money, have the risk disclosure
  reviewed by a fintech attorney before driving real traffic. (Not legal advice.)
