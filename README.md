# Mumtalikati website

Oman's property platform with an AI agent built in. This is the new Mumtalikati website prototype, ready to host on Vercel from GitHub.

It is a static site: plain HTML, CSS and JavaScript. There is nothing to install and no build step.

## What's inside

```
index.html            Page shell (all pages are drawn by app.js)
assets/css/styles.css All styling: brand colours, layout, mobile rules
assets/js/app.js      Pages, sample listings, news, AI search, agent demos
assets/js/photos.js   List of property photos and their descriptions
images/               Property photos (WebP)
icons/                Favicon and app icons
og-image.png          Preview image shown when the link is shared
site.webmanifest      Lets phones "Add to Home Screen"
vercel.json           Vercel settings: caching and security headers
404.html              Sends unknown addresses back to the home page
robots.txt            Allows search engines
```

Pages use addresses like `#/owners` and `/#/property/15`, so they all work on any static host without extra server rules.

## Preview on your computer

Open a terminal in this folder and run one of these, then open http://localhost:3000 (or the address it prints):

```
npx serve .
```

or, if you have Python:

```
python3 -m http.server 3000
```

All file paths are relative, so the same files also work on GitHub Pages or inside a subfolder.

## Step 1: Put it on GitHub

**Option A, in the browser (no tools needed)**

Already uploaded the zip by mistake? Open it in the repository, click the three dots (or the bin icon) and choose **Delete file**, commit, then follow the steps below.

1. Sign in at https://github.com and click **New repository**.
2. Name it, for example `mumtalikati-website`. Choose **Private** if you don't want it public. Click **Create repository**.
3. On the new repository page, click **uploading an existing file**.
4. **Unzip `mumtalikati-website.zip` on your computer first.** GitHub does not unzip files, so uploading the zip itself only stores a zip.
5. Open the unzipped `mumtalikati-website` folder, select everything inside it (Ctrl+A on Windows, Cmd+A on Mac) and drag it onto the GitHub page. Use Chrome or Edge, which upload folders such as `assets` and `images` by drag and drop.
6. Wait until every file is listed, then click **Commit changes**.
7. Check the repository's main page: you should see `index.html`, `vercel.json` and the `assets`, `images` and `icons` folders at the top level, not inside another folder.

Note: files whose names start with a dot (`.gitignore`) may be hidden on your computer. The site works without it.

**Option B, with Git**

```
cd mumtalikati-website
git init
git add .
git commit -m "Mumtalikati website prototype"
git branch -M main
git remote add origin https://github.com/YOUR-ACCOUNT/mumtalikati-website.git
git push -u origin main
```

## Step 2: Host it on Vercel

1. Sign in at https://vercel.com with your GitHub account.
2. Click **Add New** then **Project**, and pick the `mumtalikati-website` repository. Allow Vercel to access it if asked.
3. On the setup screen:
   - **Framework Preset:** Other
   - **Root Directory:** leave as is (`./`)
   - **Build Command:** leave empty
   - **Output Directory:** leave empty
4. Click **Deploy**. After about a minute you get a live address like `mumtalikati-website.vercel.app`.

From now on, every change pushed to the `main` branch on GitHub goes live automatically. Changes on other branches get their own preview address, which is handy for reviewing before going live.

**Option C, Vercel from the terminal**

```
npm i -g vercel
cd mumtalikati-website
vercel          # first time: answers a few questions and makes a preview
vercel --prod   # publishes to the live address
```

## Step 3: Use a Mumtalikati domain (optional)

Start with a subdomain such as `new.mumtalikati.com`, so the current site keeps running while the owner reviews the new one.

1. In Vercel, open the project, then **Settings** then **Domains**, and add the domain.
2. Vercel shows the exact DNS record to add (usually a CNAME for a subdomain).
3. Add that record at the company that manages the mumtalikati.com DNS. It usually works within minutes, sometimes a few hours.

Only point the main `mumtalikati.com` domain here once the owner approves the switch.

## Making changes

| To change | Edit |
| --- | --- |
| Colours, spacing, fonts | `assets/css/styles.css` (brand colours are at the top, under `:root`) |
| Listings, prices, areas | The `P_ALL` list in `assets/js/app.js` |
| News items | The `NEWS` list in `assets/js/app.js` |
| Agent feed on the home page | The `PMS_FEED` list in `assets/js/app.js` |
| Portals offered on "List free" | The `PORTALS` list in `assets/js/app.js` |
| A property photo | Replace the file in `images/` with the same name, or add a new file and list it in `assets/js/photos.js` |

Commit and push the change, and Vercel publishes it.

## Before this goes public

This is a working prototype for review, not the finished product.

- **No backend yet.** Searches, offers, viewings, sign-ups and portal posting run in the browser with sample data. Nothing is saved or sent. The real site should connect these to the Mumtalikati platform and its API.
- **Photos.** Some photos came from other agencies and carry their watermarks. Replace them with Mumtalikati's own photos before launch.
- **Claims.** Check every AI agent feature on the site against the live product, and label anything not yet available as coming soon.
- **Portal posting.** Publishing to OpenSooq, Bayut, Dubizzle and others needs agreements with each portal. Never auto-post where a portal's terms forbid it.
- **Legal.** Confirm the licence position under Oman's Real Estate Regulation Law, and have the news section reviewed.
- **Arabic.** The full right-to-left Arabic version is still to be built.
- **Search engines.** Pages are drawn in the browser, so Google mainly sees the home page. For SEO, the production build should generate real pages for listings and news (for example with Next.js on Vercel).
