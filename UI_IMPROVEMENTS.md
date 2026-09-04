# Meowncher UI/UX Improvement Plan

## Overview

This document outlines the systematic improvements to Meowncher's user interface and experience. The goal is to create a modern, cohesive, and delightful launcher while maintaining the performance and reliability that users expect.

## Phase 1: Rebranding ✅ COMPLETE

- [x] Update application name and display strings
- [x] Update desktop/metadata files
- [x] Update window titles and about dialogs
- [x] Update UI text references
- [x] Create new application ID and branding files
- [x] Update README and user-facing documentation

**Status**: Core rebranding complete. Binary is now "meowncher" and displays "Meowncher" throughout the UI.

## Phase 2: Foundation - Design System & Theming

### 2.1 Create Consistent Color Scheme
**Priority**: High | **Effort**: Medium | **Impact**: High

Current state: Multiple themes (Bright, Dark, Fusion, CatPack) exist but may be inconsistent.

Improvements needed:
- Define a unified color palette with Meowncher's warm tan/brown colors
- Create light and dark theme variants
- Ensure WCAG AA contrast compliance
- Add accent colors for states (success, warning, error)

**Files to modify**:
- `launcher/ui/themes/BrightTheme.cpp/h`
- `launcher/ui/themes/DarkTheme.cpp/h`
- New: `launcher/ui/themes/MeownchlerTheme.cpp/h` (primary Meowncher theme)

### 2.2 Standardize Component Styling
**Priority**: High | **Effort**: High | **Impact**: High

Current state: Individual components styled inconsistently.

Improvements needed:
- Create QSS (Qt StyleSheets) files for consistent button, input, and dialog styling
- Implement consistent spacing and padding
- Use medium corner radius (8px) throughout
- Add proper focus indicators for accessibility

**Files to modify/create**:
- `launcher/ui/resources/stylesheets/` (new directory)
- `launcher/ui/resources/stylesheets/buttons.qss`
- `launcher/ui/resources/stylesheets/inputs.qss`
- `launcher/ui/resources/stylesheets/dialogs.qss`
- `launcher/ui/resources/stylesheets/menus.qss`

### 2.3 Implement Proper State Management
**Priority**: High | **Effort**: Medium | **Impact**: Medium

Ensure all interactive elements have clear visual feedback for:
- Default state
- Hover state
- Pressed/active state
- Focused state (keyboard navigation)
- Disabled state

## Phase 3: Instance Management Redesign

### 3.1 Enhance Instance Cards/List Items
**Priority**: High | **Effort**: High | **Impact**: Very High

Current state: Basic 48px icon + text display.

Improvements needed:
- Larger, more visually interesting cards
- Display key information at a glance:
  - Instance name (large, clear)
  - Minecraft version (badge)
  - Mod loader (badge with icon)
  - Last played date
  - Instance status (running/crashed/updating)
- Better hover and selection states
- Contextual right-click menu
- Smooth animations when states change

**Files to modify**:
- `launcher/ui/instanceview/InstanceDelegate.cpp/h`
- `launcher/ui/instanceview/InstanceView.cpp/h`
- `launcher/ui/instanceview/VisualGroup.cpp/h`

**Design mockup**:
```
┌─────────────────────────────────────┐
│ 🎮 My Awesome Modpack              │  ← Name
│ Minecraft 1.20.1 | Forge 47.2       │  ← Version + Loader
│ Last played: 3 days ago             │  ← Last played
│ ■ Running | Has updates available   │  ← Status
└─────────────────────────────────────┘
```

### 3.2 Implement Search & Filtering
**Priority**: Medium | **Effort**: Medium | **Impact**: High

Current state: May not have search/filter capabilities for large instance lists.

Improvements needed:
- Real-time instance search
- Filter by: loader, status, version, tags
- Sort by: name, date played, date created, version
- Save filter/sort preferences

**Files to modify**:
- `launcher/ui/MainWindow.cpp/h`
- `launcher/ui/MainWindow.ui`
- `launcher/ui/instanceview/InstanceProxyModel.cpp/h`

### 3.3 Add Instance Tags & Groups
**Priority**: Medium | **Effort**: High | **Impact**: High

Allow users to organize instances better:
- Assign custom tags (e.g., "Survival", "Modded", "Testing")
- Group instances by tags
- Color-code tags
- Filter/search by tags
- Visual grouping in the interface

### 3.4 Multi-Selection & Bulk Actions
**Priority**: Low | **Effort**: High | **Impact**: Medium

Enable management of multiple instances at once:
- Shift+Click for range selection
- Ctrl+Click for individual selection
- Bulk delete with confirmation
- Bulk update mods
- Bulk backup

## Phase 4: Main Window & Navigation

### 4.1 Improve Main Window Layout
**Priority**: Medium | **Effort**: Medium | **Impact**: High

Current state: Standard window with sidebar or toolbar.

Improvements needed:
- Cleaner header with app name and key buttons
- Optional collapsible sidebar for better space usage
- Clear content area with proper padding
- Responsive layout for small windows
- Remember window size and position

**Files to modify**:
- `launcher/ui/MainWindow.cpp/h`
- `launcher/ui/MainWindow.ui`
- `launcher/ui/GuiUtil.cpp/h`

### 4.2 Improve Menus
**Priority**: Low | **Effort**: Medium | **Impact**: Low

- Cleaner menu organization
- Better menu icons
- Keyboard shortcuts display
- Context menus with proper styling

## Phase 5: Dialog Improvements

### 5.1 Standardize Dialog Design
**Priority**: Medium | **Effort**: Medium | **Impact**: Medium

- Consistent dialog chrome (title, close button)
- Proper padding and spacing
- Clear button hierarchy (primary/secondary)
- Focus on first input
- Escape key to cancel

**Dialogs to improve**:
- About dialog
- Preferences/Settings
- Instance creation wizard
- Mod installation
- Instance export/import

### 5.2 Instance Creation Wizard
**Priority**: High | **Effort**: High | **Impact**: High

Current state: May not have optimal UX for new users.

Improvements needed:
- Clear step-by-step workflow
- Step 1: Minecraft version (with search, recommended versions highlighted)
- Step 2: Mod loader (if desired)
- Step 3: Java runtime (with automatic detection)
- Step 4: Memory allocation (with recommended values)
- Step 5: Instance name and icon
- Summary before creation
- Progress indication during creation

## Phase 6: Settings & Preferences

### 6.1 Reorganize Settings
**Priority**: Medium | **Effort**: Medium | **Impact**: Medium

Current state: Settings may be disorganized or unclear.

Improvements needed:
- Clear categories/sections
- Search functionality
- Separate general settings from advanced settings
- Inline help/explanations
- Visual indicators for non-default values
- Reset to defaults option

**Suggested structure**:
- General (language, theme, startup behavior)
- Minecraft (launcher accounts, authentication)
- Java (runtime management, memory)
- Appearance (theme, icons, custom colors)
- Advanced (logging, cache, network)
- About (version, updates, credits)

## Phase 7: Animations & Micro-interactions

### 7.1 Add Subtle Animations
**Priority**: Low | **Effort**: Medium | **Impact**: Low

Make the interface feel more polished:
- Page transitions (200ms fade)
- Button press feedback (100ms scale)
- Instance list item animations
- Loading spinners
- Notification animations

Keep performance in mind - only animate transform/opacity.

### 7.2 Loading States
**Priority**: Medium | **Effort**: Low | **Impact**: Medium

- Show progress during long operations
- Estimated time when available
- Cancelable operations where applicable
- Graceful handling of network timeouts

## Phase 8: Accessibility Improvements

### 8.1 Keyboard Navigation
**Priority**: High | **Effort**: Medium | **Impact**: High

- Tab through all controls in logical order
- Arrow keys for list navigation
- Enter to select/activate
- Escape to cancel/close
- Alt+key for menu access

### 8.2 Focus Indicators
**Priority**: High | **Effort**: Low | **Impact**: Medium

- Visible focus indicators on all interactive elements
- High contrast focus rings
- Clear focus order

### 8.3 Screen Reader Support
**Priority**: Medium | **Effort**: High | **Impact**: Medium

- Proper ARIA labels
- Semantic HTML structure (in QML components)
- Image alt text
- Meaningful button labels

## Phase 9: Performance Optimization

### 9.1 UI Rendering Performance
- Virtualize long lists (only render visible items)
- Cache pixmaps for instance icons
- Lazy load images
- Profile and optimize paint events

### 9.2 Memory Usage
- Avoid loading all instances at startup
- Cache loaded data appropriately
- Clean up resources properly

## Phase 10: Cat Theme & Personality

### 10.1 Cute Visual Elements
**Priority**: Low | **Effort**: Low | **Impact**: Medium

Add subtle cat-inspired touches:
- Custom cursor (optional)
- Loading spinner (cat paw)
- Empty state illustrations
- Success state with cute cat
- Easter eggs and fun details

**Example**: When all instances are closed, show a sleeping cat and "Time to rest? 😺"

### 10.2 Friendly Microcopy
**Priority**: Low | **Effort**: Low | **Impact**: Low

Use friendly, clear language:
- "Create a new cozy setup" instead of "Create instance"
- "Your instances are all set!" instead of generic success
- Helpful error messages with solutions

## Implementation Strategy

### Priority Order
1. **Phase 1: Rebranding** ✅ DONE
2. **Phase 2: Foundation** (Design System & Theming)
3. **Phase 3.1-3.2**: Instance Management (Search, Enhanced Cards)
4. **Phase 5.2**: Instance Creation Wizard
5. **Phase 4**: Main Window Layout
6. **Phase 5.1**: Dialog Standardization
7. **Phase 6**: Settings Reorganization
8. **Phase 3.3-3.4**: Advanced Instance Features (Tags, Bulk Actions)
9. **Phase 7-8**: Animations & Accessibility
10. **Phase 9-10**: Performance & Polish

### Testing Strategy
- Unit tests for new components
- Visual regression testing for UI changes
- Accessibility audit with keyboard navigation
- Performance profiling before/after changes
- User feedback during development

### Branch Strategy
- Work in feature branches
- Create PRs for review
- Test on multiple platforms (Linux, Windows, macOS)
- Maintain backward compatibility with existing instances

## Success Criteria

- **Usability**: New users can create and launch an instance without help
- **Performance**: UI remains responsive with 100+ instances
- **Accessibility**: WCAG 2.1 AA compliance
- **Polish**: Consistent visual design throughout
- **Reliability**: No regressions in existing functionality
- **Code Quality**: Well-organized, documented, maintainable code
