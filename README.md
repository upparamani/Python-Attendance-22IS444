# 📋 Attendance System — KLS Gogte Institute of Technology

> Serverless, real-time student attendance system for the ISE Department  
> Built for \*\*Python Programming (22IS444) · 2025–26\*\*

🔗 **Live:** 
Professor URL: https://upparamani.github.io/Python-Attendance-22IS444/index6.html?prof=1
Student URL: https://upparamani.github.io/Python-Attendance-22IS444/index6.html

\---

## ✨ Features

* 🔐 **Dual-mode interface** — separate Professor and Student screens from a single URL
* 🎟️ **Token-based verification** — professor generates a 4-digit token per session; students must enter it to mark attendance
* ⏱️ **Auto-closing sessions** — 5-minute countdown timer; session closes automatically when time runs out
* ⏸️ **Pause / Resume** — professor can pause the session (students cannot mark while paused)
* 📡 **Real-time live table** — professor dashboard polls every 2 seconds and shows who has marked attendance
* 🔔 **Toast notifications** — professor sees a flashing name alert every time a student marks attendance
* 📊 **Export to Excel** — beautifully formatted `.xlsx` with institution headers, rotated date columns, colour-coded P/A cells
* ☁️ **Serverless** — no backend server; data stored on [JSONbin.io](https://jsonbin.io)
* 📱 **Mobile-friendly** — students can mark attendance from any phone browser

\---

## 🖼️ Screenshots

Login Screen

|<img width="908" height="468" alt="image" src="https://github.com/user-attachments/assets/006f8062-76c6-4ade-89e4-994dca3875df" />

Student Screen

|<img width="960" height="359" alt="image" src="https://github.com/user-attachments/assets/99ad749d-660b-4b7d-bee4-b7f00a92b0af" />

Professor Dashboard

|<img width="924" height="351" alt="image" src="https://github.com/user-attachments/assets/acbdb194-5750-4b6f-aa6a-151a35a4550c" />


Live Attendance Table

|<img width="935" height="193" alt="image" src="https://github.com/user-attachments/assets/4101d8c4-c454-4ad9-9ea5-3cf5a1b89e7c" />

Exported Excel

|<img width="1056" height="612" alt="image" src="https://github.com/user-attachments/assets/4ddb5319-ed93-4558-a2ee-baa31a36563e" />


\---

## ⚙️ How It Works

```
Professor opens ?prof=1 URL
        │
        ▼
Professor clicks Open → token generated → stored in JSONbin
        │
        ▼
Students open the same URL → enter USN + token → attendance marked in JSONbin
        │
        ▼
Professor dashboard polls JSONbin every 2s → live table updates + toast fires
        │
        ▼
Session closes (manual or timer) → record saved to sessions\[] array
        │
        ▼
Professor exports Excel → styled register downloaded
```

**Two screens, one file:**

* Default URL → Student screen only
* `?prof=1` appended → Professor card appears (kept hidden from students)

\---

## 🚀 Setup \& Deployment

### 1\. Clone the repo

```bash
git clone https://github.com/upparamani/Attendance2.git
cd Attendance2
```

### 2\. Add your student list

Edit `students.js` — define a `STUDENTS` array:

```js
const STUDENTS = \[
  { id: "2KG22IS001", name: "Student Name" },
  { id: "2KG22IS002", name: "Student Name" },
  // ...
];
```

### 3\. Set up JSONbin

1. Create a free account at [jsonbin.io](https://jsonbin.io)
2. Create a new bin with initial value: `{"sessions":\[],"activeSession":null}`
3. Copy your **Bin ID** and **Master Key**
4. Update in `index6.html`:

```js
const BIN\_ID  = "your\_bin\_id\_here";
const API\_KEY = "your\_master\_key\_here";
```

### 4\. Deploy to GitHub Pages

1. Push all files to your repo
2. Go to **Settings → Pages → Source → main branch → / (root)**
3. Your live URL will be:

   * Students: `https://upparamani.github.io/Attendance2/index6`
   * Professor: `https://upparamani.github.io/Attendance2/index6?prof=1`

> ⚠️ \*\*Keep the `?prof=1` URL private\*\* — share only the plain URL with students.

\---

## 📁 File Structure

```
Attendance2/
│
├── index6.html        # Main application (all logic in one file)
├── students.js        # Student list — USN + Name array
├── style.css          # UI styles (dark theme)
└── README.md          # This file
```

\---

## 🛠️ Tech Stack

|Layer|Technology|
|-|-|
|Frontend|HTML5, CSS3, Vanilla JavaScript|
|Data storage|[JSONbin.io](https://jsonbin.io) (free REST API)|
|Excel export|[xlsx-js-style](https://github.com/gitbrent/xlsx-js-style) v1.2.0|
|Hosting|GitHub Pages (static, free)|
|Backend|None — fully serverless|

\---

## 📌 Usage Notes

* One session can be open at a time
* A student can mark attendance only once per session
* Sessions are permanently saved in JSONbin under `sessions\[]`
* Excel export includes **all past sessions** — run it at any time to get the full register
* The 5-minute timer is for the token window only; the professor can close/reopen manually

\---

## 👨‍🏫 Author

**Pandurang Shankar Upparamani**  
Assistant Professor, ISE Department  
KLS Gogte Institute of Technology, Belagavi

\---

*Built with plain HTML/JS — no frameworks, no servers, no cost.*

