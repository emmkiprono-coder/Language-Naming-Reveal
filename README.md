# Language Services Reveal Page

Standalone single page reveal experience with password gate, multi-stage reveal animations, pledge prompt, and shared pledge wall powered by JSONBin.

## What's in this folder

- `index.html` - the reveal page itself, single file, no build step
- `create_bin.html` - one-click utility that provisions the pledge bin
- `README.md` - this file

## Setup (90 seconds, one time)

1. Open `create_bin.html` in your browser. Click the big button. It creates a public JSONBin under the existing committee portal API key and shows you the bin ID.
2. Open `index.html` in any text editor. Find this line near the top of the script block:
   ```js
   pledgesBin: "REPLACE_WITH_PLEDGES_BIN_ID"
   ```
   Replace the placeholder with the bin ID from step 1.
3. While you are in there, fill in the winning name and submitter details:
   ```js
   winningName: "...",
   submitterName: "...",
   submitterDepartment: "...",
   meaningRationale: "...",
   howItUnifies: "..."
   ```
4. Save.

## Deploy

Push the folder to GitHub, point Vercel at it, done. No build, no server, no environment variables. The page is fully static and talks to JSONBin from the browser.

## How the pledge wall works

When someone submits a pledge, the page reads the current bin, removes any prior pledge from that same name (case insensitive), prepends the new one, and writes the updated array back. Newest pledges appear first on the wall. Per device pledges are also stashed in localStorage so the form stays in the shared state on refresh.

## Password

`BRIDGE`, case insensitive. To change, edit `password` in the CONFIG block.
