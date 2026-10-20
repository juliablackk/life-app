# My App
 
A personal organizer that brings my day into one place: tasks, events, workouts, habits, and meal prep, with a Home screen that shows today at a glance.
 
I'm building this for my own daily use and as a portfolio project to practice backend development, database design, and testing.
 
> **Status:** In planning. The Tasks section is designed; development starts next.
 
## Features
 
| Section | What it does | Status |
|---|---|---|
| **Tasks** | Weekly calendar of to-dos, multi-day tasks, custom categories, completion tracking, Upcoming and Undated lists | Designed |
| **Home** | Today's date, a time-based greeting, and today's tasks, events, and workouts | Planned |
| **Events** | Calendar of events by category (school, work, travel, parties) | Planned |
| **Exercise** | Exercise library by muscle group, weekly plan, weight and rep logging, analytics | Planned |
| **Habits** | Sleep tracking with analytics, daily log of what I watched or read | Planned |
| **Meal prep** | Weekly meal prep ideas with nutrition info, protein goal tracking, grocery lists | Planned |
 
## Tech stack
 
- **Backend:** Python, FastAPI
- **Database:** SQLite
- **Frontend:** HTML, CSS, JavaScript (mobile-friendly)
- **Testing:** pytest
- **CI:** GitHub Actions
## Design decisions
 
### Tasks
 
- **Completion is tracked per day.** A task can be assigned to several dates, and each date has its own checkbox.
- **Overall status is calculated, not stored.** A task is *completed* when every assigned day is checked, *partially completed* when some are, and *not started* when none are. Deriving it from the daily checkboxes means it can never get out of sync.
- **Day colors:** green if checked, red if unchecked and past due, otherwise the category's color (gray if uncategorized).
- **Categories are custom and optional,** shared between tasks and events. Colors come from a preset palette that excludes green and red so they're never confused with status. Deleting a category moves its items to "No category."
- **Undated tasks** appear in their own list. A task is undated when it has no assigned days.
### Data model (Tasks)
 
```
Category 1 ──── * Task 1 ──── * TaskDay
  (optional link)      (cascade delete)
```
 
- **Category:** id, name (unique), color, created_at
- **Task:** id, title, notes, category_id (nullable, set null on delete), overall_due_date (nullable), created_at
- **TaskDay:** id, task_id, date, completed, completed_at. Each task + date pair is unique.
## Getting started
 
_Setup instructions will be added once the first endpoint is built._
 
## Roadmap
 
1. Tasks
2. Home
3. Events
4. Exercise
5. Habits
6. Meal prep
 
