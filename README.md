📋 Attendance System — KLS Gogte Institute of Technology
> Serverless, real-time student attendance system for the ISE Department  
> Built for **Python Programming (22IS444) · 2025–26**
🔗 Live: upparamani.github.io/Attendance2/index6
---
✨ Features
🔐 Dual-mode interface — separate Professor and Student screens from a single URL
🎟️ Token-based verification — professor generates a 4-digit token per session; students must enter it to mark attendance
⏱️ Auto-closing sessions — 5-minute countdown timer; session closes automatically when time runs out
⏸️ Pause / Resume — professor can pause the session (students cannot mark while paused)
📡 Real-time live table — professor dashboard polls every 2 seconds and shows who has marked attendance
🔔 Toast notifications — professor sees a flashing name alert every time a student marks attendance
📊 Export to Excel — beautifully formatted `.xlsx` with institution headers, rotated date columns, colour-coded P/A cells
☁️ Serverless — no backend server; data stored on JSONbin.io
📱 Mobile-friendly — students can mark attendance from any phone browser
---
🖼️ Screenshots
Login Screen	Student Screen	Professor Dashboard
(screenshot)	(screenshot)	(screenshot)

Live Attendance Table	Exported Excel
(screenshot)	(screenshot)
---
⚙️ How It Works
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
Session closes (manual or timer) → record saved to sessions[] array
        │
        ▼
Professor exports Excel → styled register downloaded
```
Two screens, one file:
Default URL → Student screen only
`?prof=1` appended → Professor card appears (kept hidden from students)
---
🚀 Setup & Deployment
1. Clone the repo
```bash
git clone https://github.com/upparamani/Attendance2.git
cd Attendance2
```
2. Add your student list
Edit `students.js` — define a `STUDENTS` array:
```js
const STUDENTS = [
  { id: "2KG22IS001", name: "Student Name" },
  { id: "2KG22IS002", name: "Student Name" },
  // ...
];
```
3. Set up JSONbin
Create a free account at jsonbin.io
Create a new bin with initial value: `{"sessions":[],"activeSession":null}`
Copy your Bin ID and Master Key
Update in `index6.html`:
```js
const BIN_ID  = "your_bin_id_here";
const API_KEY = "your_master_key_here";
```
4. Deploy to GitHub Pages
Push all files to your repo
Go to Settings → Pages → Source → main branch → / (root)
Your live URL will be:
Students: `https://upparamani.github.io/Attendance2/index6`
Professor: `https://upparamani.github.io/Attendance2/index6?prof=1`
> ⚠️ **Keep the `?prof=1` URL private** — share only the plain URL with students.
---
📁 File Structure
```
Attendance2/
│
├── index6.html        # Main application (all logic in one file)
├── students.js        # Student list — USN + Name array
├── style.css          # UI styles (dark theme)
└── README.md          # This file
```
---
🛠️ Tech Stack
Layer	Technology
Frontend	HTML5, CSS3, Vanilla JavaScript
Data storage	JSONbin.io (free REST API)
Excel export	xlsx-js-style v1.2.0
Hosting	GitHub Pages (static, free)
Backend	None — fully serverless
---
📌 Usage Notes
One session can be open at a time
A student can mark attendance only once per session
Sessions are permanently saved in JSONbin under `sessions[]`
Excel export includes all past sessions — run it at any time to get the full register
The 5-minute timer is for the token window only; the professor can close/reopen manually
---
👨‍🏫 Author
Pandurang Shankar Upparamani  
Assistant Professor, ISE Department  
KLS Gogte Institute of Technology, Belagavi
---
Built with plain HTML/JS — no frameworks, no servers, no cost.
