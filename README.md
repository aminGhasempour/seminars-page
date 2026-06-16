# Joint Statistical Seminars page

This folder contains a simple static seminar website that can be served with GitHub Pages.

## Files

- `index.html` — the website layout, styling, filtering, search, modal details, and calendar download code.
- `seminars.js` — the seminar data. Edit this file when you want to add, remove, or update seminars.

Keep both files in the same folder.

## Publish with GitHub Pages

1. Create a GitHub repository, for example `seminars-page`.
2. Upload these files to the root of the repository:

   ```text
   index.html
   seminars.js
   README.md
   ```

3. In the repository, go to **Settings → Pages**.
4. Under **Build and deployment**, choose:

   ```text
   Source: Deploy from a branch
   Branch: main
   Folder: /root
   ```

5. Click **Save**.

After GitHub finishes deploying, your page should be available at:

```text
https://YOUR-GITHUB-USERNAME.github.io/YOUR-REPOSITORY-NAME/
```

Example:

```text
https://aghasempour.github.io/seminars-page/
```

## Add a new seminar

Open `seminars.js`. Add a new seminar object inside the `window.SEMINARS = [ ... ];` list.

Example:

```js
{
  id: "2026-11-17-speaker-name",
  title: "Seminar title goes here",
  date: "2026-11-17",
  startTime: "13:00",
  endTime: "14:00",
  timezone: "Europe/Stockholm",
  speaker: "Speaker Name",
  affiliation: "University or Department",
  venue: "SAM.A.241",
  abstract: "Write the abstract here. Use plain text.",
  tags: ["Statistics"]
}
```

Important: add a comma between seminar entries.

Correct:

```js
window.SEMINARS = [
  {
    id: "2026-09-01-first-seminar",
    title: "First seminar",
    date: "2026-09-01",
    startTime: "13:00",
    endTime: "14:00",
    timezone: "Europe/Stockholm",
    speaker: "First Speaker",
    affiliation: "Department of Statistics",
    venue: "SAM.A.257",
    abstract: "To be announced",
    tags: ["Statistics"]
  },
  {
    id: "2026-09-15-second-seminar",
    title: "Second seminar",
    date: "2026-09-15",
    startTime: "13:00",
    endTime: "14:00",
    timezone: "Europe/Stockholm",
    speaker: "Second Speaker",
    affiliation: "Department of Statistics",
    venue: "SAM.A.343",
    abstract: "To be announced",
    tags: ["Statistics"]
  }
];
```

## Required seminar fields

Each seminar should have these fields:

| Field | Example | Notes |
|---|---|---|
| `id` | `2026-09-01-ye-tian` | Must be unique. Use lowercase letters, numbers, and hyphens if possible. |
| `title` | `To be announced` | The seminar title. |
| `date` | `2026-09-01` | Use `YYYY-MM-DD`. |
| `startTime` | `13:00` | Use 24-hour time. |
| `endTime` | `14:00` | Use 24-hour time. Needed for calendar downloads. |
| `timezone` | `Europe/Stockholm` | Usually keep this unchanged. |
| `speaker` | `Ye Tian` | Speaker name. |
| `affiliation` | `Department of Statistics` | Speaker affiliation. |
| `venue` | `SAM.A.257` | Room or location. |
| `abstract` | `To be announced` | Plain text abstract. |
| `tags` | `["Statistics"]` | List of topics. |

## Upcoming vs previous seminars

The page automatically decides whether a seminar is upcoming or previous by comparing the seminar date with today's date.

- Future dates appear under **Upcoming**.
- Past dates appear under **Previous**.

## Test locally

For a quick local test, open `index.html` in your browser.

For the most realistic test before publishing, run a simple local server from the folder:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000/
```

## Common problems

### The page loads but seminars do not appear

Check that:

- `index.html` and `seminars.js` are in the same folder.
- The file is named exactly `seminars.js`.
- `seminars.js` starts with:

  ```js
  window.SEMINARS = [
  ```

- `seminars.js` ends with:

  ```js
  ];
  ```

- There is a comma between seminar entries.
- You did not accidentally use smart quotes like `“ ”` instead of normal quotes `"`.

### GitHub Pages shows an old version

GitHub Pages can take a little time to update after changes. Refresh the page, or try opening it in a private/incognito browser window.

### OneDrive does not load `seminars.js`

OneDrive is not recommended for hosting this two-file version. Use GitHub Pages or another static website host. If you must use OneDrive, use the single-file version where seminar data is inside `index.html`.
