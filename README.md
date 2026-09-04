# Component Bins — setup guide

This is a single file (`index.html`) — everything (layout, styling, logic) lives inside it. There's nothing to install and nothing to build.

## 1. Put it on GitHub Pages (5 minutes)

1. Go to github.com and create a **new repository** (any name, e.g. `component-bins`). Public is fine — nothing sensitive is in the code itself.
2. Upload `index.html` to the repo (drag-and-drop on the repo's "Add file → Upload files" page works fine).
3. In the repo, go to **Settings → Pages**.
4. Under "Build and deployment", set **Source** to "Deploy from a branch", branch = `main`, folder = `/ (root)`. Save.
5. Wait a minute, then your app is live at `https://<your-username>.github.io/<repo-name>/`.

That's the whole hosting step — no domain purchase, no server.

## 2. Connect it to a data file (so your inventory syncs across devices)

The app stores your inventory as one JSON file inside a GitHub repo (can be the same repo as the site, or a separate one — your choice).

1. Create a **Personal Access Token** so the app can write to that repo:
   - Go to github.com → your profile photo → **Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**.
   - Give it a name like "component bins app".
   - Under **Repository access**, choose "Only select repositories" and pick the repo you'll store data in.
   - Under **Permissions → Repository permissions**, set **Contents** to "Read and write".
   - Generate the token and copy it (you won't be able to see it again — if you lose it, just make a new one).
2. Open your deployed app, click **"GitHub sync…"** in the sidebar.
3. Fill in:
   - **Repo owner**: your GitHub username
   - **Repo name**: the repo you want to store `inventory.json` in
   - **Branch**: usually `main`
   - **File path**: leave as `data/inventory.json` (or change it)
   - **Personal access token**: paste the token from step 1
4. Click **"Load from GitHub"**. Since the file doesn't exist yet, it'll offer to create it — say yes.

From then on:
- Any edits you make are kept in the browser (and backed up automatically to your browser's local storage as a draft) until you click **"Save to GitHub"** (top right) or press **Ctrl/Cmd+S**.
- On another device (or another browser), open the app, go to GitHub sync, fill in the same details, and click "Load from GitHub" to pull your latest saved inventory.

## Notes

- The token is stored only in your browser's local storage — it never leaves your machine except when talking directly to GitHub's API.
- Because writes happen on an explicit "Save" click, it's normal to make several edits and then save once.
- Every save is a normal git commit, so your GitHub repo's commit history doubles as a full edit history / backup of your inventory — you can always look at an old commit if you ever need to recover something.
