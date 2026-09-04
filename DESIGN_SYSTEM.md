/**
 * Meowncher Design System
 * 
 * This document defines the visual and interaction design principles for Meowncher.
 * The design system ensures consistency across the application while maintaining
 * performance and accessibility.
 */

/**
 * COLOR PALETTE
 * 
 * Primary Colors (Meowncher Brand):
 * - Primary: #D4A574 (warm tan/cat color)
 * - Secondary: #8B7355 (deep brown)
 * - Accent: #E8A87C (lighter tan for highlights)
 * 
 * Semantic Colors:
 * - Success: #4CAF50 (green)
 * - Warning: #FF9800 (orange)
 * - Error: #F44336 (red)
 * - Info: #2196F3 (blue)
 * 
 * Neutrals (Light Theme):
 * - Background: #FFFFFF
 * - Surface: #F5F5F5
 * - Text Primary: #212121
 * - Text Secondary: #757575
 * - Border: #E0E0E0
 * - Disabled: #BDBDBD
 * 
 * Neutrals (Dark Theme):
 * - Background: #121212
 * - Surface: #1E1E1E
 * - Text Primary: #E0E0E0
 * - Text Secondary: #A0A0A0
 * - Border: #333333
 * - Disabled: #606060
 */

/**
 * TYPOGRAPHY
 * 
 * Font Family: System Default (for performance)
 * - Uses platform native fonts for best performance
 * - Fallback: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif
 * 
 * Sizes and Weights:
 * - Display: 32px, Weight 500
 * - Title: 24px, Weight 500
 * - Heading: 18px, Weight 500
 * - Subheading: 14px, Weight 500
 * - Body Large: 16px, Weight 400
 * - Body: 14px, Weight 400
 * - Body Small: 12px, Weight 400
 * - Caption: 11px, Weight 400
 * 
 * Line Height:
 * - Headings: 1.3
 * - Body: 1.5
 */

/**
 * SPACING
 * 
 * Base unit: 4px
 * 
 * Spacing Scale:
 * xs: 4px   (2 units)
 * sm: 8px   (2 units)
 * md: 12px  (3 units)
 * lg: 16px  (4 units)
 * xl: 24px  (6 units)
 * xxl: 32px (8 units)
 * 
 * Usage:
 * - Dialog margins: xl (24px)
 * - Section padding: lg (16px)
 * - Item spacing: md (12px)
 * - Element gaps: sm (8px)
 * - Micro spacing: xs (4px)
 */

/**
 * CORNER RADIUS
 * 
 * - Sharp: 0px (buttons, inputs in compact mode)
 * - Small: 4px (small controls, badge badges)
 * - Medium: 8px (cards, buttons, text inputs)
 * - Large: 12px (dialogs, panels)
 * - Full: 999px (rounded pills, circular badges)
 * 
 * Default for most elements: 8px
 */

/**
 * SHADOWS & ELEVATION
 * 
 * Surface Elevation:
 * - Flat (0): No shadow
 * - Raised (1): 0 2px 4px rgba(0,0,0,0.1)
 * - Card (2): 0 4px 8px rgba(0,0,0,0.12)
 * - Floating (3): 0 8px 16px rgba(0,0,0,0.15)
 * - Modal (4): 0 16px 32px rgba(0,0,0,0.2)
 * 
 * Dark Theme: Increase opacity by ~40%
 */

/**
 * COMPONENT STATES
 * 
 * All interactive components should have clear states:
 * 
 * Button States:
 * - Default: Standard appearance
 * - Hover: Slightly lighter/darker background
 * - Pressed: Darker background, slight inset
 * - Disabled: 50% opacity, cursor: not-allowed
 * - Focus: Blue ring (2px, #2196F3) at 2px offset
 * 
 * Input States:
 * - Empty: Border color
 * - Focused: Accent color border, shadow
 * - Filled: Standard appearance
 * - Error: Red border, error icon
 * - Disabled: Gray background, no interaction
 * 
 * Instance Card States:
 * - Default: Clean appearance
 * - Hover: Subtle background lift, shadow increase
 * - Selected: Accent border, highlight background
 * - Running: Green indicator, active styling
 * - Crashed: Red indicator, error styling
 * - Updating: Progress indicator
 */

/**
 * ANIMATIONS & TRANSITIONS
 * 
 * Duration:
 * - Micro: 100ms (hover states, small elements)
 * - Short: 200ms (typical interactions)
 * - Medium: 300ms (dialogs, major changes)
 * - Long: 500ms (page transitions, complex animations)
 * 
 * Easing:
 * - Ease In/Out: cubic-bezier(0.4, 0, 0.2, 1)
 * - Decelerate: cubic-bezier(0, 0, 0.2, 1)
 * - Accelerate: cubic-bezier(0.4, 0, 1, 1)
 * - Linear: for progress indicators
 * 
 * Performance:
 * - Only animate transform and opacity
 * - Avoid animating layout properties
 * - Use 60fps animations
 * - Provide reduced-motion preferences
 */

/**
 * RESPONSIVE DESIGN
 * 
 * Breakpoints:
 * - Mobile: < 600px (single column)
 * - Tablet: 600px - 1200px (adaptive layout)
 * - Desktop: > 1200px (full layout)
 * 
 * Principles:
 * - Mobile-first approach
 * - Touch-friendly hit areas (min 48px)
 * - Adapt font sizes and spacing
 * - Maintain core functionality on all sizes
 */

/**
 * ACCESSIBILITY
 * 
 * Contrast:
 * - Text on background: 4.5:1 minimum (WCAG AA)
 * - UI components: 3:1 minimum
 * 
 * Focus Indicators:
 * - Always visible
 * - High contrast
 * - Clear keyboard navigation path
 * 
 * Labels & Descriptions:
 * - All inputs have associated labels
 * - Icons have tooltips
 * - Buttons have descriptive text
 * - Long content has summaries
 * 
 * Motion:
 * - Respect prefers-reduced-motion
 * - Provide disable options for animations
 * - No auto-playing content
 */

/**
 * MEOWNCHER-SPECIFIC ELEMENTS
 * 
 * Cat Theme Integration:
 * - Subtle cat silhouettes in decorative areas
 * - Cat-inspired icon set
 * - Warm, cozy color palette
 * - Friendly, approachable microcopy
 * - Easter eggs and personality
 * 
 * Empty States:
 * - Include simple cat illustration
 * - Friendly message explaining the state
 * - Clear call-to-action
 * - Example: "No instances yet. Time to create your first cozy setup!"
 * 
 * Loading States:
 * - Cat paw loading animation
 * - Progress indication
 * - Estimated time when available
 * 
 * Success States:
 * - Happy cat illustration
 * - Confirmatory message
 * - Next steps suggestion
 */

/**
 * COMPONENT LIBRARY
 * 
 * The following reusable components should be implemented:
 * 
 * Buttons:
 * - Primary (filled)
 * - Secondary (outlined)
 * - Tertiary (text-only)
 * - Compact variant
 * - Icon buttons
 * 
 * Cards:
 * - Instance cards with status
 * - Information cards
 * - Statistics cards
 * 
 * Dialogs:
 * - Confirmation
 * - Alert
 * - Input
 * - Settings
 * - Full-screen (for complex workflows)
 * 
 * Inputs:
 * - Text field
 * - Dropdown/Combobox
 * - Checkbox
 * - Radio button
 * - Toggle switch
 * - Slider
 * 
 * Lists:
 * - Item list
 * - Sortable list
 * - Filterable list
 * 
 * Navigation:
 * - Menu bar
 * - Sidebar (collapsible)
 * - Tab bar
 * - Breadcrumbs
 * 
 * Feedback:
 * - Toast notifications
 * - Inline messages (info, warning, error, success)
 * - Progress bars
 * - Loading spinners
 */

/**
 * LAYOUT PATTERNS
 * 
 * Main Window:
 * - Header: Application title and main controls
 * - Sidebar: Navigation and instance list
 * - Content: Main workspace
 * - Footer: Status and version info (optional)
 * 
 * Instance Management:
 * - Search/filter bar
 * - Instance grid or list
 * - Context menu on right-click
 * - Bulk action toolbar when selected
 * 
 * Settings:
 * - Category sidebar
 * - Settings content area
 * - Search across settings
 * - Apply/Reset/OK buttons
 * 
 * Dialogs:
 * - Clear title
 * - Organized content
 * - Action buttons aligned right
 * - Proper focus management
 */
