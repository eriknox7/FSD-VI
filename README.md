# PrepTrack — jQuery Mobile App

**Practical No. 06 · jQuery Mobile**
*Create a simple Mobile Website using jQuery Mobile.*

PrepTrack is a mobile-first web app for tracking DSA / placement-prep problems. It is built as a single-file, multi-page jQuery Mobile application with a custom dark theme, and stores all data in the browser using `localStorage`.

---

## Features

| Page | What it does |
|------|--------------|
| **Dashboard** | Daily-goal progress ring, solved / streak / pending stats, bar charts by difficulty and topic, recently solved list |
| **Problems** | Search, status filter (All / Todo / Revisit / Solved), tap for action popup, swipe right to mark solved |
| **Add / Edit** | Form with title, link, topic, difficulty, status and notes |
| **Settings** | Name, daily goal slider, motivational-message toggle, load sample data, export JSON, reset |

Extras: persistent data (`localStorage`), UNDO toast after delete, streak calculation, custom bottom navigation bar, floating action button.

---

## Tech Stack

- HTML5, CSS3 (custom properties, flexbox, grid)
- jQuery 1.11.3
- jQuery Mobile 1.4.5
- Browser `localStorage` (no backend)

jQuery and jQuery Mobile are loaded from the official CDN (`code.jquery.com`), so an **internet connection is required** on first load.

---

## How to Run

1. Download `preptrack_jquery_mobile.html`.
2. Open it in any modern browser (Chrome / Edge / Firefox).
3. Switch to mobile view: press **F12**, then **Ctrl + Shift + M** (Chrome / Edge) and pick a phone size.
4. Optional: open **Settings → Load sample problems** to see the app with data.

No installation or build step needed.

---

## jQuery Mobile Concepts Used

| Concept | Where used |
|---------|-----------|
| Multi-page structure (`data-role="page"`) | Dashboard, Problems, Add, Settings in one file |
| Header / Footer (`data-position="fixed"`) | Top bar and bottom navigation |
| Navbar (`data-role="navbar"`) | Bottom tab bar, injected into each page |
| Panel (`data-role="panel"`) | Side menu |
| Popup (`data-role="popup"`) | Problem actions, reset confirmation |
| Listview (`data-role="listview"`) | Problem list, recent list |
| Controlgroup | Status filter, difficulty and status radios |
| Form widgets | Text, URL, select menu, textarea, slider, flipswitch |
| Page transitions | `changePage()` with `slideup`, `slidedown`, `fade` |
| Events | `pagebeforecreate`, `pagebeforeshow`, `pagehide`, `swiperight` |

### Important note on dynamic content

jQuery Mobile enhances markup only once. When content is generated with JavaScript, widgets must be refreshed manually, otherwise they appear unstyled:

```js
$("#problemList").html(html).listview("refresh");
$("#fTopic").val("Arrays").selectmenu("refresh");
$("input[name=diff]").checkboxradio("refresh");
```

---

## Project Structure

```
preptrack_jquery_mobile.html   # complete app (HTML + CSS + JS)
README.md
```

### Data model

```json
{
  "problems": [
    {
      "id": "p1700000000000",
      "title": "Two Sum",
      "link": "https://leetcode.com/problems/two-sum/",
      "topic": "Arrays",
      "diff": "easy",
      "status": "solved",
      "notes": "Use a hash map",
      "createdAt": 1700000000000,
      "solvedOn": "2026-10-08",
      "solvedAt": 1700000500000
    }
  ],
  "settings": { "name": "", "goal": 3, "motiv": "on" }
}
```

Stored under the `localStorage` key `preptrack_v1`.

---

## Screenshots to Include in Report

1. Dashboard (with sample data loaded)
2. Problems list with search / filter
3. Action popup on a problem
4. Add Problem form
5. Settings page
6. Side panel menu

---

## Limitations

- Data lives only in the current browser; use **Export as JSON** for a backup.
- Requires internet for the CDN-hosted libraries.
- jQuery Mobile 1.4.5 is no longer actively developed; this project is for learning the framework.

---

## Author

**Sadique Khan** — B.Tech CSE (Data Science), MIT Academy of Engineering, Pune
