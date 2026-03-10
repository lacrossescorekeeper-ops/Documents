# Lacrosse ScoreKeeper

A comprehensive iOS app for tracking lacrosse games in real-time, built with SwiftUI and SwiftData.

## Overview

Lacrosse ScoreKeeper is a full-featured scorekeeping application designed for coaches, players, and fans to track every aspect of a lacrosse game. From live scoring and penalty tracking to detailed player statistics and game events, this app provides everything needed to manage and analyze lacrosse games.

## Features

### 📊 Game Management

#### Game Creation & Setup
- Create new games with customizable settings
- Set opponent name, date, time, and location
- Choose between quarters (4x12 min) or halves (2x30 min)
- Configure period duration and overtime length
- Track game status: Scheduled → In Progress → Final

#### Game List View
- Organized sections for In Progress, Upcoming, and Completed games
- Live indicator with pulsing animation for active games
- Quick access to game scores and dates
- Swipe-to-delete functionality
- Color-coded status badges

### 🏃 Live Scoring

#### Real-Time Game Clock
- Full game clock with start/pause/reset controls
- Automatic countdown with visual warnings (red text under 60 seconds)
- Period/quarter tracking with overtime support
- Manual time adjustment (+10s / -10s)
- Quick quarter selection menu
- **Auto-save every 10 seconds** - Clock state is automatically persisted

#### Player Identification System
- Numeric keypad for quick jersey number entry
- Team selector (Home/Opponent)
- Automatic player lookup by jersey number
- Support for unknown players (unrecognized jersey numbers)
- Team-level events (no specific player)
- Visual confirmation with player name display

#### Event Tracking
Record comprehensive game events:
- **Offensive:** Goals, Assists, Shots
- **Defensive:** Saves, Caused Turnovers
- **Possession:** Ground Balls, Turnovers
- **Face-offs:** Won/Lost
- **Clears:** Success/Fail
- **Man-Up:** EMO Goal, EMO Fail

#### Live Events Feed
- Real-time event list displayed under keypad (50% width layout)
- Most recent events shown first (reverse chronological)
- Quarter dividers (Q1, Q2, Q3, Q4, OT, OT2, etc.)
- Color-coded event icons:
  - 🟢 Green: Positive events (goals, assists, saves)
  - 🟠 Orange: Negative events (turnovers, failed clears)
  - 🔵 Blue: Neutral home team events
  - 🔴 Red: Opponent events
- Event details: Player name, action type, game time
- Long-press context menu to delete events

#### Penalty Management
- Add penalties with detailed information:
  - Foul type (Technical/Personal)
  - Duration (30sec, 1min, 2min, 3min)
  - Player assignment (Home/Opponent)
  - Quarter and game time stamp
- **Real-time penalty countdown** - Ticks down with game clock
- Active penalties display in header with time remaining
- Visual warnings (orange text under 30 seconds)
- Quick release button for man-down goals
- Release early functionality via swipe actions
- Automatic expiration when time runs out
- Penalty history view with all recorded penalties

#### Scoreboard & Header
Comprehensive game information always visible:
- Live game clock with current quarter/period
- Team scores (Home vs Opponent)
- Active penalties with countdown timers
- Timeout tracking for both teams
- Quick access to penalties view

#### Navigation & Data Safety
- **Back button with auto-save** - Automatically pauses clock and saves state
- **Auto-save timer** - Game state saved every 10 seconds
- **Swipe-to-go-back support** - Standard iOS gesture with data persistence
- State restoration - Return to exact game state when reopening
- Multiple save points prevent data loss

### 📈 Statistics & Analytics

#### Player Statistics
- Individual player performance tracking
- Season-wide statistics:
  - Goals, Assists, Points
  - Shots, Shot Percentage
  - Ground Balls
  - Turnovers, Caused Turnovers
  - Saves (for goalies)
  - Face-off Win/Loss/Percentage
  - Penalties
- Game-by-game performance history
- Sortable by various statistics

#### Team Statistics
- Aggregate team performance
- Win/Loss record
- Total goals scored vs allowed
- Possession statistics
- Penalty tracking
- Clear success rate
- Face-off performance

#### Game Details
- Complete game summary
- Final scores and outcome
- Event timeline with quarter breakdowns
- Penalty summary
- Location and date information
- Start/end game controls

### 👥 Roster Management

#### Player Database
- Create and manage team roster
- Track player information:
  - First and last name
  - Jersey number
  - Position (Attack, Midfield, Defense, Goalie, LSM, FOGO)
  - Active/inactive status
- Quick player search and filtering
- Add/edit/delete players
- Player performance across all games

#### Opponent Players
- Automatic creation for opponent jersey numbers
- Track opponent statistics separately
- Game-specific opponent tracking

### ⚙️ Technical Features

#### Data Persistence
- **SwiftData** for local database storage
- **Auto-save functionality** every 10 seconds during live games
- Automatic state restoration
- Data migration support
- Cascade delete relationships (deleting game removes all events/penalties)

#### User Interface
- **Professional blue & gray color scheme** optimized for lacrosse branding
- Custom color palette:
  - **Backgrounds**: Blue-gray dark theme (`.bg`, `.bgSurface`, `.bgCard`, `.bgElevated`)
  - **Text**: High-contrast hierarchy (`.textPrimary`, `.textSecondary`, `.textMuted`)
  - **Brand Colors**: 
    - `.accent` - Primary blue (#2196f3) for main actions
    - `.blue` - Dark blue (#1976d2) for home team
    - `.gray` - Blue-gray (#607d8b) for neutral elements
    - `.green` - Green (#4caf50) for positive events
    - `.red` - Red (#f44336) for opponent/penalties
    - `.amber` - Orange (#ff9800) for warnings
- Responsive layouts with 50/50 split views
- Haptic feedback for user interactions
- SwiftUI animations and transitions
- Monospaced fonts for numbers/times
- WCAG AA compliant contrast ratios for accessibility

#### Data Models
- **Game** - Game information, clock state, scores
- **GameEvent** - Individual game actions
- **Penalty** - Penalty tracking with countdown
- **Player** - Team roster members
- **OpponentPlayer** - Opponent roster tracking

#### Clock Management
- `GameClock` class with timer functionality
- Tick callbacks for penalty countdown
- State persistence (quarter & time)
- Flexible period configuration

### 🎯 User Experience

#### Intuitive Controls
- Large, touch-friendly buttons
- Visual feedback for all actions
- Confirmation dialogs for critical actions
- Error prevention (duplicate events, invalid data)

#### Real-Time Updates
- Live score updates
- Instant event recording
- Automatic penalty countdowns
- Visual status indicators

#### Quick Actions
- One-tap event recording
- Swipe gestures for common actions
- Keyboard shortcuts for number entry
- Context menus for secondary actions

## App Structure

```
Lacrosse ScoreKeeper/
├── App Entry
│   └── Lacrosse_ScoreKeeperApp.swift
│
├── Views/
│   ├── MainTabView.swift           # Main tab navigation
│   ├── GamesListView.swift         # Game list with sections
│   ├── GameDetailView.swift        # Game info and controls
│   ├── LiveScoringView.swift       # Real-time scoring interface
│   ├── PenaltiesView.swift         # Penalty management
│   ├── RosterView.swift            # Player management
│   ├── NewGameView.swift           # Game creation form
│   ├── PlayerFormView.swift        # Add/edit players
│   ├── TeamStatsView.swift         # Team statistics
│   └── PlayerStatsView.swift       # Player statistics
│
├── Models/
│   ├── Game.swift                  # Game data model
│   ├── GameEvent.swift             # Event data model
│   ├── Penalty.swift               # Penalty data model
│   ├── Player.swift                # Player data model
│   ├── OpponentPlayer.swift        # Opponent player model
│   └── GameClock.swift             # Clock logic
│
└── Utilities/
    └── Color+Extensions.swift       # Custom color palette
```

## Data Flow

### Auto-Save System

The app implements a comprehensive auto-save system to prevent data loss:

1. **Timer-Based Auto-Save (10 seconds)**
   - Runs continuously while Live Scoring view is active
   - Saves game clock state (quarter, time remaining)
   - Saves timestamp of last save
   - Lightweight, non-intrusive

2. **User-Initiated Save**
   - Triggered when tapping Back button
   - Pauses clock automatically
   - Saves all game state
   - Provides haptic feedback

3. **View Lifecycle Save**
   - Triggered on view disappear
   - Catches swipe-back gestures
   - Final safety net for data persistence

4. **Event-Based Save**
   - Each event, penalty, or score change is immediately persisted
   - SwiftData handles automatic persistence
   - No manual save button required

### State Restoration

When returning to a live game:
- Clock resumes at exact saved time and quarter
- All events and penalties are loaded
- Penalty countdowns continue from saved state
- Scores reflect all recorded events

## Technical Requirements

- **Platform:** iOS 17.0+
- **Language:** Swift 6.0
- **Framework:** SwiftUI
- **Database:** SwiftData
- **Architecture:** MVVM with observable models

## Future Enhancements

Potential features for future development:
- [ ] Shot charts (location tracking)
- [ ] Export game statistics (PDF/CSV)
- [ ] Share game results
- [ ] Multi-team management
- [ ] Cloud sync (iCloud)
- [ ] iPad optimization
- [ ] Apple Watch companion app
- [ ] Live game sharing/spectator mode
- [ ] Video integration
- [ ] Advanced analytics and charts
- [ ] Season/tournament tracking

## Development Notes

### Key Design Decisions

1. **SwiftData Over Core Data**
   - Modern Swift-first approach
   - Simplified data modeling with macros
   - Better SwiftUI integration
   - Type-safe queries

2. **Custom Clock Implementation**
   - Game-specific timing requirements
   - Penalty countdown integration
   - Manual time adjustments for officials
   - State persistence for interruptions

3. **Split Layout (50/50)**
   - Keypad + Events on left (50%)
   - Action buttons on right (50%)
   - Prevents scroll conflicts
   - Optimizes for one-handed operation

4. **Jersey Number Keypad**
   - Faster than picker/list
   - Muscle memory for coaches
   - Supports unknown players
   - Team events without player selection

5. **Auto-Save Strategy**
   - 10-second intervals balance data safety with performance
   - Multiple save triggers prevent data loss
   - Clock state persistence enables game interruptions
   - No user interaction required

### Performance Considerations

- Lazy loading for event lists
- Efficient filtering of active penalties
- Minimal re-renders during clock ticks
- Optimized SwiftData queries

### Error Handling

- Model container creation with cleanup fallback
- Safe SwiftData persistence with try/catch
- Optional clock state for backward compatibility
- Graceful handling of missing players

## Credits

Created by Jeffrey Eckerlin (February 2026)

Built with SwiftUI and SwiftData for iOS

---

**Last Updated:** February 22, 2026

---

## App Store Information

### App Name
Lacrosse ScoreKeeper

### Subtitle
Live Game Stats & Scoring

### App Description

Lacrosse ScoreKeeper is the ultimate sideline companion for coaches, parents, and fans who want to track every detail of a lacrosse game in real time.

**Live Scoring Made Simple**
Use the jersey number keypad to instantly record goals, assists, saves, ground balls, turnovers, and more — all with a single tap. The split-screen layout keeps the action moving without fumbling through menus.

**Real-Time Game Clock & Penalties**
A full game clock counts down each period with automatic overtime support. Active penalties display live countdowns right in the scoreboard header, so you always know when your team is man-up or man-down — with EMO notifications to keep you in the game.

**Comprehensive Player & Team Stats**
Track individual player performance across every game: goals, assists, shots, shot percentage, ground balls, face-off wins, saves, and more. View season-wide team statistics including win/loss record, clear success rate, and possession stats.

**Detailed Game Summaries**
Review completed games with full event timelines broken down by quarter, penalty summaries, and scoring breakdowns for both teams.

**Built for the Sideline**
- Large, touch-friendly buttons designed for outdoor use
- Auto-save every 10 seconds so you never lose data
- Haptic feedback confirms every action
- Dark-themed interface reduces glare in bright sunlight
- Works entirely offline — no internet required

Whether you're a coach breaking down film, a parent keeping the book, or a fan who wants more than just the final score — Lacrosse ScoreKeeper has you covered.

### Keywords

lacrosse, scorekeeping, score keeper, stats, statistics, live scoring, game clock, coach, penalty tracker, box score

### App Store Categories
- **Primary:** Sports
- **Secondary:** Utilities
