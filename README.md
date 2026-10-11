🎓 Bachelor Buddy (v1.0)

The all-in-one offline-first Progressive Web App (PWA) crafted for Indian college bachelors, hostellers, and flatmates.

Bachelor Buddy unites personal finance, college academics, and shared apartment expenses into a cohesive, Apple iOS 18-inspired interface. Built with pure vanilla web standards, it runs without build tools, functions completely offline, and synchronizes seamlessly across devices via Firebase.

🌟 Key Features

🏠 1. Personal Dashboard & Apple iOS 18 Widgets

Interactive iOS Widget Grid:

1×1 & 2×1 Squircles: Frosted glass materials (backdrop-filter: blur(28px)), continuous 24px squircle curves, and top-edge specular glass reflections.

Long-Press Jiggle Mode: Press and hold any widget on the Home screen (~500ms) or tap the edit icon to enter iOS Edit Mode.

Drag & Drop Rearranging: Reorder widgets via intuitive drag-and-drop or 1-tap ▲ (Move Upper) and ▼ (Move Lower) buttons on mobile.

Dynamic Resizing: Tap ⤢ to instantly toggle widgets between 1×1 (Small Square) and 2×1 (Big Banner).

Quick Spend Circular Ring: Live spending circle with real-time glowing shadows:

🟢 Green Glow: On track (< 70% of daily safe limit).

🟡 Amber Glow: Near safe limit (70% – 100%).

🔴 Red Glow & Alert: Over daily budget (> 100%).

1-Tap Presets: Fast logging buttons (+10, +20, +30, and custom prompt), customizable in Widget Settings.

Habits Activity Ring: Circular completion ring displaying today's completed habit ratio (e.g. 2/3), active streak counter, and dynamic rating badges (🏆 GREAT CHAMP, ⚡ AVERAGE, 🌱 READY TO START).

Direct Item Logging: 1-tap [+ 1] and [-1] controls directly on the Home widget for your active custom item (Cigarettes, Chai, Coffee, etc.).

Budget Tracking: Real-time daily safe spending limits calculated based on your monthly budget allowance.

7 Theme Engine: Switch between Obsidian, Monochrome Titanium, Emerald, Sunset, Cyberpunk, Ocean, and OLED Black.

🎓 2. College Academic Hub

Focus Study Timer:

Live ticking session clock with streak tiers.

Automatic midnight day rollover reset back to 00:00:00.

Exam Prep & "This Unit, This Day" Planner:

Track Semester and Competitive exams (GATE, CAT, UPSC).

Days remaining countdown and pending syllabus unit velocity calculations (e.g., 1 unit every 4 days).

Dedicated Study Planner: Map each pending syllabus unit to a specific target date and time.

1-Tap Auto-Planner: Automatically spaces pending units evenly across the days remaining before exams.

Phone Alarms & Notifications: Audio chime alarm (AudioContext) and phone notification alerts at scheduled study session times.

Attendance & 75% Bunk Simulator:

Live attendance percentage dial with safe bunks remaining or classes needed to hit 75%.

Weekly routine timetable with 1-tap [✓ Present] and [✗ Bunked] logging.

Editable pre-app baseline attendance to account for past records.

Automatic Saturday & Sunday weekend badges.

Syllabus Tracker: Unit-by-unit check-off checklist synced with semester selectors.

Assignment Deadlines: Due-date countdowns and urgent submission alerts.

CGPA & SGPA Calculator: Semester-wise credit point and cumulative grade point average estimator.

🤝 3. Flat & Roommate Expense Split

Rasan Grocery Pool:

Shared apartment monthly grocery pool balance tracker.

Over-budget carry-forward warnings showing exact deduction amounts for next month's pool.

Inline grocery entry editing ([✏ Edit]) and deletion ([✕ Delete]).

1-Tap WhatsApp Summary: Formatted text summary ready to post in your flatmates' WhatsApp group.

Clean Printable PDF Statements: Generates an isolated, standalone printable statement with budget summaries, net balances, and itemized purchase tables with zero clipping.

Kharcha Bill Splitter: Split recurring apartment expenses (Rent, Maid, Wi-Fi, Electricity) equally among flatmates.

Debts & Khata Ledger: Peer-to-peer debt ledger with automated balance netting between roommates.

🛠 Tech Stack & Architecture

Frontend: Vanilla HTML5, Modern CSS (CSS Grid, Flexbox, Glassmorphism, CSS Custom Properties), Vanilla JavaScript (ES6+).

Storage & Sync:

Offline-First: Client-side storage via localStorage ensures full offline capability.

Cloud Sync: Firebase Authentication (Google Sign-In) and Cloud Firestore for multi-device synchronization.

Data Overwrite Safeguard: hasData() protection prevents empty devices from overwriting populated cloud documents upon sign-in.

Backup & Restore: 1-click JSON data export and import in Settings.

Audio & Alarms: Web Audio API oscillator synthesis (playAlarmChime()) for reliable device chimes.

PWA & Notifications: Web Notifications API, Service Worker (sw.js) with network-first caching and notification click handlers.

📁 Repository Structure

.
├── index.html         # Complete single-file application (UI, logic, and styles)
├── sw.js              # Service Worker for offline caching & notifications
├── manifest.json      # PWA Web App Manifest for homescreen installation
├── config.js          # Firebase project credentials
├── app_icon_512.png   # 512x512 PWA Application Icon
├── icon.png           # 192x192 PWA Application Icon
└── README.md          # Project documentation


🚀 Quick Deployment Guide

1. Deploy on Vercel

Fork or push this repository to your GitHub account (e.g. aditya5393/bachelor-buddy).

Go to Vercel and click Add New Project.

Select your bachelor-buddy repository.

Leave the build settings as default (No Build Command, Output Directory: ./).

Click Deploy. Vercel will serve your app at https://your-project.vercel.app.

2. Configure Firebase (For Cloud Sync)

Create a project at the Firebase Console.

Enable Authentication with Google Sign-In.

Enable Cloud Firestore and configure your security rules to secure user data:

rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}


Copy your web app config object into config.js:

window.FIREBASE_CONFIG = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};


3. Install as a PWA

Android (Chrome): Tap the three dots menu ⋮ → Add to Home screen / Install app.

iOS (Safari): Tap the Share button ⎋ → Add to Home Screen.

🔒 Privacy & Data Safety

Zero Tracker Policy: Bachelor Buddy contains no analytics trackers, tracking cookies, or third-party ad networks.

User-Isolated Storage: Every user's data is isolated to their own authenticated user ID document.

Manual Data Portability: Full JSON export and import options are available at any time in Settings.

📄 License

This project is open-source and available under the MIT License.
