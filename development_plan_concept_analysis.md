# Study Timetable Planner: Concept Analysis & AI Development Plan

## 1. Executive Summary & Concept Analysis

### 1.1 Product Vision
The **Study Timetable Planner** is an interactive, aesthetic web productivity application that translates traditional paper paper-planner habits into a digital workspace. It combines **micro-level daily scheduling** (8:00 – 18:00 hourly blocks), **macro-level monthly goal tracking**, and **qualitative daily reflections** with built-in productivity utilities (Pomodoro timer, procedural ambient rain sound generator, and visual progress tracking).

### 1.2 UX & Visual Design Principles
* **Pastel Sky Aesthetic:** Low-contrast soft blues (`#70caf9`, `#cbe7fb`), soft whites, and emerald accents designed to minimize visual fatigue during long study sessions.
* **Paper-Digital Hybrid Feel:** Analog design motifs—such as spiral rings, notebook-dotted lines, paperclip accents, and mood emojis—create an inviting, low-stress planning environment.
* **Frictionless Data Entry:** Auto-saving via browser LocalStorage eliminates the need for manual save buttons or account login barriers.

### 1.3 Core Features & Functional Requirements
1. **Dynamic Daily Schedule:**
   - 11 default hourly slots (8:00 to 18:00) with editable task fields.
   - Instant completion toggling with progress bar calculations.
   - Custom time slot addition and slot deletion.
2. **Monthly Focus Objectives:**
   - Objective list with dotted notebook aesthetics.
   - Goal completion checkboxes and task management.
3. **Daily Reflection & Mood Tracker:**
   - Lined notebook area for key takeaways and daily summaries.
   - Interactive emoji mood/energy rating system.
4. **Productivity Utilities:**
   - **Pomodoro Timer Modal:** Customizable Focus (25m), Short Break (5m), and Long Break (15m) timers.
   - **Procedural Audio Generator:** Web Audio API Brownian noise synthesis mimicking ambient rain (no external audio files required).
   - **Data Management:** Date picker switching, sample data pre-loader, and print-ready CSS export.

---

## 2. Technical Architecture & Tech Stack

| Layer | Recommended Technology | Rationale |
| :--- | :--- | :--- |
| **Markup & Structure** | HTML5 / Single File Bundle | Easy to distribute, embed, or preview without build pipelines. |
| **Styling** | Tailwind CSS (v3 CDN) + Custom CSS | Rapid layout utility classes combined with custom CSS gradients and spiral ring keyframes. |
| **Typography & Icons** | FontAwesome 6 + Google Fonts (`Fredoka`, `Inter`) | Soft display fonts for headers and clear sans-serif body text. |
| **State Management** | Vanilla JavaScript (ES6+) with LocalStorage | Zero-dependency reactive state pattern keyed by date strings (`study_timetable_YYYY-MM-DD`). |
| **Audio Synthesis** | HTML5 Web Audio API | Zero external assets needed for ambient rain sounds and completion chimes. |

---

## 3. Phase-by-Phase Development Plan (Claude Iterative Workflow)

Follow this multi-phase roadmap when prompting Claude to build or expand the application from scratch.

```
       +-------------------------------------------------------+
       | PHASE 1: Layout & Aesthetic Shell                     |
       | - Grid layout (Daily vs Goals vs Summary)             |
       | - Custom Tailwind config & paper graphics             |
       +---------------------------+---------------------------+
                                   |
                                   v
       +-------------------------------------------------------+
       | PHASE 2: State Model & LocalStorage Persistence       |
       | - Dynamic task rendering                              |
       | - Date switcher & LocalStorage keying                 |
       +---------------------------+---------------------------+
                                   |
                                   v
       +-------------------------------------------------------+
       | PHASE 3: Monthly Goals & Reflection Notebook          |
       | - Dotted line CSS rendering                           |
       | - Mood state selector & notes auto-save               |
       +---------------------------+---------------------------+
                                   |
                                   v
       +-------------------------------------------------------+
       | PHASE 4: Audio Engine & Pomodoro Timer               |
       | - Web Audio API Brownian noise generator              |
       | - Countdown timer with modal controls                 |
       +---------------------------+---------------------------+
                                   |
                                   v
       +-------------------------------------------------------+
       | PHASE 5: Print Export & Edge Case QA                   |
       | - `@media print` styling overrides                     |
       | - Mobile responsiveness tweaks                        |
       +-------------------------------------------------------+
```

---

## 4. Claude Prompt Sequence (Step-by-Step Copy/Paste Prompts)

### Phase 1 Prompt: Layout Shell & Tailored Aesthetic
> **Prompt:**  
> "Act as a Senior Frontend Developer. Create a single-file HTML document using Tailwind CSS (CDN) and FontAwesome icons that replicates a paper study planner template. Set up a pastel blue background gradient (`#bfe3fc` to `#e2f2fe`). The layout must contain:  
> 1. Header with title 'Study Timetable Planner', date input, and action buttons.  
> 2. Progress banner showing completed vs total hourly tasks with a progress bar.  
> 3. Two-column main section: 7-col daily hourly schedule (8:00 to 18:00) on the left, 5-col 'Monthly Focus' card on the right.  
> 4. Bottom full-width 'Today Summary' card designed to look like a spiral-bound notebook with rings at the top.  
> Include custom CSS for spiral rings, notebook dotted lines, and clean scrollbars."

---

### Phase 2 Prompt: Dynamic Timetable & LocalStorage State
> **Prompt:**  
> "Now add Vanilla JavaScript state management to the application.  
> 1. Define a state object for tasks `[{ id, time, text, completed }]`, monthly goals, summary, and mood.  
> 2. Store state in `localStorage` under keys formatted as `study_timetable_YYYY-MM-DD`.  
> 3. When the date picker changes, dynamically load that specific day's data or initialize default hours (8:00 - 18:00).  
> 4. Add functions to edit task text, toggle completion (updating progress bar percentage in real-time), delete task rows, and add extra time slots dynamically."

---

### Phase 3 Prompt: Goal Tracker, Reflection Notebook, & Mood Selector
> **Prompt:**  
> "Implement interactive logic for the Monthly Focus and Today Summary sections:  
> 1. Monthly Focus: allow adding new goal items with an input field, toggling completion, and deleting goals. Style each goal with a dotted bottom border line.  
> 2. Today Summary: auto-save text changes from the textarea into `localStorage`.  
> 3. Mood Tracker: add a row of 5 mood emojis (😍, 😊, 😐, 🥱, 😫) where clicking one sets the active mood state with a visual pop/scale animation."

---

### Phase 4 Prompt: Web Audio API Rain & Pomodoro Timer Modal
> **Prompt:**  
> "Add two productivity utilities using zero external library dependencies:  
> 1. Focus Audio Generator: use the HTML5 Web Audio API to procedurally generate a soothing brownian/pink noise algorithm mimicking rain audio when toggled on/off.  
> 2. Pomodoro Timer: create a clean modal with Focus (25m), Short Break (5m), and Long Break (15m) modes. Include start/pause/reset controls, audio chime synthesis on completion, and reflect the remaining time in a top header pill."

---

### Phase 5 Prompt: Export, Sample Data, & Print Tweaks
> **Prompt:**  
> "Finalize the application with polishing features:  
> 1. Add a 'Preset' button to pre-fill realistic study tasks and notes for demonstration.  
> 2. Add a 'Reset' button with a confirmation popup.  
> 3. Add a temporary toast notification system for feedback (e.g., 'Progress updated!').  
> 4. Add `@media print` styles so that printing the page hides non-essential buttons/modals and renders a clean, printable physical worksheet."

---

## 5. Testing & Verification Checklist

- [ ] **Date Switching:** Selecting different dates loads independent timetable configurations without data bleed.
- [ ] **LocalStorage Validation:** Task updates, checkbox states, and notebook notes persist upon refreshing the browser.
- [ ] **Web Audio Permissions:** Clicking "Focus Audio" initiates audio context smoothly after user interaction (avoiding browser autoplay blocks).
- [ ] **Mobile Responsiveness:** Daily schedule stacks neatly into a single column on screen widths below 768px.
- [ ] **Print Layout:** Invoking `window.print()` outputs a crisp single/double page without modal overlays or background noise buttons.