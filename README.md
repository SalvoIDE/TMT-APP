# TMT-APP
October 30, 2025

Trail Making Test — Offline Edition (TMT)
=========================================
Developer Technical Documentation
Version: 2025.10
Author: SLCucinella
License: Research and Educational Use Only

------------------------------------------------------------
1. OVERVIEW
------------------------------------------------------------
This application implements a fully offline, browser-based version
of the Trail Making Test (TMT) — a standard neuropsychological task
used to assess processing speed and cognitive flexibility.

The project is designed to run locally or via GitHub Pages without
server dependencies. All data is saved locally on the user's device.

Supported Devices:
- iPad (iOS ≥ 10.3.3)
- Modern desktop browsers (Safari, Chrome, Firefox, Edge)

------------------------------------------------------------
2. PROJECT STRUCTURE
------------------------------------------------------------
The app consists of a single HTML file with embedded CSS and JS logic:
- index.html         → Main app file (UI + logic)
- README_TMT_IT.txt  → End-user instructions (Italian)
- README_TMT_EN.txt  → End-user instructions (English)
- README_TMT_DEV.txt → Developer documentation

No external dependencies or frameworks are required.

------------------------------------------------------------
3. LOGIC OVERVIEW
------------------------------------------------------------
The application workflow follows four sequential tasks:

  Practice A → TMT-A → Practice B → TMT-B

Each task:
- Loads a fixed set of node coordinates (2048×1536 logical space)
- Draws numbered circles in a fixed order
- Tracks touch or mouse input events
- Logs every valid click, elapsed time, and inter-click delta
- Saves results in three local file formats:
    [ParticipantID]_[TaskType]_[YYYY-MM-DD].csv
    [ParticipantID]_[TaskType]_[YYYY-MM-DD].txt
    [ParticipantID]_[TaskType]_[YYYY-MM-DD].json

------------------------------------------------------------
4. DATA HANDLING AND SECURITY
------------------------------------------------------------
- Data is stored temporarily in the browser’s localStorage.
- Upon completion, three output files are generated.
- Files are automatically opened in a new tab for saving via:
    "Share → Save to Files" (on iPad)
- No external network connections or APIs are used.
- Only Participant ID is collected (no personal data).

------------------------------------------------------------
5. CODE SECTIONS
------------------------------------------------------------
Core JS sections in index.html:
1. Constants and UI elements
2. Layout definitions per task type
3. Event listeners (start, tap, save)
4. Drawing logic (Canvas API)
5. Data logging and CSV/JSON/TXT generation
6. Automatic file download via Blob / data URI

------------------------------------------------------------
6. CUSTOMIZATION
------------------------------------------------------------
Developers can safely modify:
- Circle coordinates for each task (layouts object)
- Circle radius and color (in draw() function)
- Timing and logging fields (log.push() structure)
- UI text labels and language

When modifying coordinates:
Ensure circles do not overlap and spacing reflects test difficulty.

------------------------------------------------------------
7. DEBUGGING
------------------------------------------------------------
For browser debugging:
- Use Chrome DevTools → Console → “Show verbose logs”
- Tap events log in real-time
- CSV export can be inspected via `console.log(createCSV())`

------------------------------------------------------------
8. FUTURE IMPROVEMENTS
------------------------------------------------------------
Suggested extensions:
- Multi-participant session tracking
- Custom difficulty randomization
- Real-time visualization of paths
- Integration with clinical data systems (offline export only)
- Automated error counting / feedback metrics

------------------------------------------------------------
9. LICENSE AND ATTRIBUTION
------------------------------------------------------------
This software is provided for academic and research purposes.
Attribution required when used in publications or teaching.

Commercial distribution or cloud hosting is prohibited
without written authorization from the author.

© 2025 Trail Making Test — Offline Edition
