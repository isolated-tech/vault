# Periodic Notes Setup Guide

## Overview
This system provides automated daily, weekly, monthly, and yearly notes to track your thoughts and goals.

## Plugin Setup

### 1. Install Periodic Notes Plugin
1. Open Obsidian Settings (⚙️)
2. Go to Community plugins
3. Browse and search for "Periodic Notes"
4. Install and enable the plugin

### 2. Configure Daily Notes
1. In Settings → Periodic Notes → Daily Notes
2. Enable Daily Notes
3. Set these options:
   - **Date Format**: YYYY-MM-DD
   - **New File Location**: Internal/Periodic Notes/Daily
   - **Template File Location**: Internal/Periodic Notes/Templates/daily-template.md
   - **Open on Startup**: Toggle on if desired

### 3. Configure Weekly Notes
1. In Settings → Periodic Notes → Weekly Notes
2. Enable Weekly Notes
3. Set these options:
   - **Date Format**: YYYY-[W]ww
   - **New File Location**: Internal/Periodic Notes/Weekly
   - **Template File Location**: Internal/Periodic Notes/Templates/weekly-template.md

### 4. Configure Monthly Notes
1. In Settings → Periodic Notes → Monthly Notes
2. Enable Monthly Notes
3. Set these options:
   - **Date Format**: YYYY-MM
   - **New File Location**: Internal/Periodic Notes/Monthly
   - **Template File Location**: Internal/Periodic Notes/Templates/monthly-template.md

### 5. Configure Yearly Notes
1. In Settings → Periodic Notes → Yearly Notes
2. Enable Yearly Notes
3. Set these options:
   - **Date Format**: YYYY
   - **New File Location**: Internal/Periodic Notes/Yearly
   - **Template File Location**: Internal/Periodic Notes/Templates/yearly-template.md

## Usage

### Creating Notes
- **Daily Note**: Use command palette (Cmd/Ctrl + P) → "Periodic Notes: Open today's daily note"
- **Weekly Note**: "Periodic Notes: Open this week's weekly note"
- **Monthly Note**: "Periodic Notes: Open this month's monthly note"
- **Yearly Note**: "Periodic Notes: Open this year's yearly note"

### Keyboard Shortcuts (Optional)
You can set custom hotkeys in Settings → Hotkeys:
- Search for "Periodic Notes"
- Assign shortcuts like:
  - Daily: Cmd/Ctrl + Shift + D
  - Weekly: Cmd/Ctrl + Shift + W
  - Monthly: Cmd/Ctrl + Shift + M
  - Yearly: Cmd/Ctrl + Shift + Y

## Template Features

### Daily Notes
- Goal tracking with checkboxes
- Morning/evening reflections
- Habit tracker
- Daily review section
- Navigation links to previous/next days

### Weekly Notes
- Professional and personal goals
- Week overview by day
- Progress tracking
- Weekly reflection
- Links to previous/next weeks

### Monthly Notes
- Comprehensive goal setting
- KPI tracking
- Project management
- Monthly reflection
- Financial tracking

### Yearly Notes
- Annual theme setting
- Major goals across life areas
- Quarterly reviews
- Financial summary
- Vision planning

## Tips
1. **Consistency**: Try to fill out your daily notes at the same time each day
2. **Review**: Use weekly/monthly reviews to adjust goals
3. **Links**: Use [[wikilinks]] to connect related notes
4. **Tags**: Add #tags for easy searching (e.g., #goal-achieved, #lesson-learned)
5. **Templates**: Customize the templates to fit your needs

## Folder Structure
```
Internal/
└── Periodic Notes/
    ├── Templates/
    │   ├── daily-template.md
    │   ├── weekly-template.md
    │   ├── monthly-template.md
    │   └── yearly-template.md
    ├── Daily/
    ├── Weekly/
    ├── Monthly/
    ├── Yearly/
    └── Setup Guide.md
```