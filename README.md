# Land Properties Register

A small web app to keep records of ancestral land across villages: area, co-owners, location, the khatauni (land record PDF), the map, and an Excel export. Data is saved in **your own private GitHub repository**.

You need two repositories:

| Repo | Visibility | Contains |
|---|---|---|
| `land-register` | Public (needed for free GitHub Pages) | Only this app (`index.html`). No personal data. |
| `land-data` | **Private** | `data.json` (all property details) and `files/` (PDFs, maps). |

## Setup (about 10 minutes)

1. **Create the data repo.** On github.com click New repository, name it `land-data`, choose **Private**, tick "Add a README file", create.
2. **Create the app repo.** New repository named `land-register`, **Public**. Click "Add file > Upload files", upload `index.html` and `README.md` from this folder, commit.
3. **Turn on the website.** In `land-register` go to Settings > Pages. Under "Build and deployment" choose Source: "Deploy from a branch", Branch: `main`, folder `/ (root)`, Save. After a minute your site is at `https://YOUR-USERNAME.github.io/land-register/`.
4. **Make a token.** GitHub > Settings > Developer settings > Personal access tokens > Fine-grained tokens > Generate new token.
   - Repository access: **Only select repositories** > `land-data`
   - Permissions: Repository permissions > **Contents: Read and write**
   - Copy the token (it is shown once).
5. **Connect the app.** Open your site, click **Settings**, enter `YOUR-USERNAME/land-data`, branch `main`, paste the token, Save. The status line at the top should say "Connected to GitHub".

From now on every add, edit, delete and file upload is committed to `land-data`. Open the same site on another device, enter the same settings, and your data appears.

## Documents tab (deeds, court cases and other papers)

Open the **Documents** tab to keep every other paper in one place: sale deeds, gift deeds, wills, partition (batwara), mutation, court cases and orders, tax receipts, maps, affidavits and more.

- Each document has a title, type, optional linked property, deed/case number, date, notes, and one or more files (PDF, photos, Word).
- Search finds matches in the title, type, reference number, notes, property name and file names. You can also filter by type or by property.
- A property's **Details** window lists the documents linked to it.
- Everything is saved in `land-data` (`docs.json` and the `files/` folder). Export Excel includes a Documents sheet.
- Search covers what you type in the fields, not the text inside scanned files, so put key names, case numbers and dates in the title or notes.

## Khatauni auto-read (no keys, no accounts)

Click **Upload khatauni (auto-fill)** and choose the PDF or a photo of the khatauni. The app reads it on your own device using free open-source OCR (Tesseract with Hindi) and fills in village, tehsil, district, khata number, gata/khasra numbers, area and co-owner names. Nothing is sent to any AI service.

- The first run downloads the Hindi language data (a few MB) and takes about a minute.
- OCR can make mistakes, so **check every field before saving**. Names and area read well on clean downloads; other numbers can slip, which is why the form is shown for review.
- The khatauni file is attached automatically as the land record.

## Safety notes

- Keep `land-data` **private**. Never make it public: it contains names and land details.
- The GitHub token (the only credential in this project) is stored only in your browser. Do not enter it on a shared or public computer. If it leaks, delete it on GitHub and make a new one.
- Every change is a Git commit, so GitHub keeps the full history of your records.
- Use "Export Excel" now and then for an extra copy.
