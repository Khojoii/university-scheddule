# 📅 Weekly Class Schedule | Dadbin Kerman Faculty

A single-file, fast, fully offline web page for displaying a weekly class schedule — no framework, no build step, no backend required. Just one `index.html` file with everything (code, styles, logo) embedded inside it.

🔗 **Demo:** once deployed on GitHub Pages, the link will look like:
`https://<username>.github.io/<repo-name>/`

---

## ✨ Features

| Section | Description |
|---|---|
| 🗓 Daily timeline | Tabs for Saturday–Wednesday, each day showing a vertical timeline of classes in chronological order |
| 🎯 "Today" detection | Today's tab is automatically highlighted based on the system date (small red dot) |
| 🔗 Back-to-back classes | When two classes run with zero gap between them, the connecting line turns gold and both dots become filled (solid) |
| ⏳ Idle time between classes | When there's a real gap between two classes, a thin dashed tile shows exactly how much free time is available |
| 📊 Stats bar | Total number of courses, total weekly class hours, and total enrolled credit units |
| 🕐 Live date & clock | Persian (Jalali) date — converted automatically from the Gregorian date — plus a 24-hour clock, updating every second |
| 🌙 Dark mode | A toggle button in the header corner switches between light and dark themes |
| 🖱 Full details on click | Clicking any class opens a modal with instructor, exact time, faculty, credit units, and exam date/time |
| 🖨 Print / Save as PDF | A button at the bottom of the page to print or export the schedule as a PDF |
| 🌐 Animated network background | A subtle canvas animation of connected dots — a nod to the fact that most courses are networking-related |
| 📱 Responsive | Displays cleanly on mobile with no horizontal scrolling |

---

## 🛠 Tech Stack

Just **HTML + CSS + Vanilla JavaScript** — no framework, no package manager, no build step. The [Vazirmatn](https://github.com/rastikerdar/vazirmatn) font is loaded from a CDN.

```
index.html   ← everything lives here (HTML, CSS, JS, logo as base64)
README.md    ← this file
```

---

## 🚀 Running Locally

No server or installation needed — just open the file:

```bash
# Option 1: open directly in the browser
open index.html        # macOS
start index.html       # Windows
xdg-open index.html    # Linux

# Option 2: serve with a lightweight local server (recommended,
# since some browsers are strict with the file:// protocol)
python3 -m http.server 8000
# then visit http://localhost:8000
```

---

## ☁️ Deploying to GitHub Pages (Free)

1. Create a new repository and push this file as `index.html` in the **repo root** (not inside a subfolder).
2. Go to **Settings → Pages** in the repository.
3. Under **Build and deployment**, set **Source** to `Deploy from a branch`, branch `main`, folder `/ (root)`.
4. Click **Save** and wait a couple of minutes.
5. The live link will appear on that same Pages settings page.

Since everything — including the logo — is embedded inside `index.html`, there are no extra files to upload.

---

## ✏️ Editing Courses

All schedule data lives in a JavaScript array called `COURSES`, inside the `<script>` tag of `index.html`. To add, edit, or remove a course, just edit this array directly:

```js
const COURSES = [
  {
    name:      "Course name",
    day:       "شنبه",        // one of: شنبه, یک‌شنبه, دوشنبه, سه‌شنبه, چهارشنبه
    start:     "09:30",        // 24-hour format
    end:       "12:30",
    teacher:   "Instructor name",
    exam:      "1405/10/19",   // exam date (Jalali/Persian calendar)
    examTime:  "08:00",
    units:     2,              // number of credit units
    color:     "#2f6fce"       // this course's card color
  },
  // ...other courses
];
```

Important: every other part of the page (tabs, stats, back-to-back detection, idle-time calculation, "today" detection) is **automatically derived from this same array** — you only need to update the data, and the rest of the UI stays in sync.

> 🔜 **Coming next:** an in-site form to add/remove courses without touching code. This is currently being designed — we still need to decide where the data should live: `localStorage` (browser-only), or a cloud database like Firebase/Supabase for cross-device sync.

---

## 🎨 Customizing the Look

The main color scheme is controlled via CSS variables at the top of the file:

```css
:root {
  --navy: #0c2f5e;     /* primary header/branding color */
  --blue: #2f6fce;     /* secondary accent color */
  --gold: #c9922c;     /* highlight color (back-to-back links, exam info) */
  ...
}
```

Dark mode has its own set of overridden variables under the `body.dark` selector.

---

## ⚠️ Limitations

- GitHub Pages is **static hosting only** — no backend or real database (SQL, etc.) is supported.
- Exam dates and course details are currently entered **manually**, not synced from a school information system.
- Gregorian-to-Jalali date conversion is done with a lightweight standard algorithm, with no external library.

---

## 📄 License

Free to use for personal or educational purposes. Feel free to modify anything you like.

---

<div align="center">
Built for Dadbin Kerman Faculty · National University of Skills
</div>
