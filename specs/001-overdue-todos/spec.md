# Specification: Support for Overdue Todo Items

## User Story

**As a** todo application user
**I want to** easily identify and distinguish overdue tasks in my todo list
**So that** I can prioritize my work and quickly see which tasks are past their due date

## Description

Users need a clear, visual way to identify which todos have not been completed by their due date. This helps users quickly spot overdue items without having to manually check dates against today's date.

## Requirements

### Functional Requirements

1. **Overdue Detection**: The system must automatically determine if a todo is overdue by comparing its due date to the current date.
2. **Visual Indicator**: Overdue todos must display a distinct visual indicator (styling and text) that clearly differentiates them from non-overdue items.
3. **Completed Items Excluded**: Todos that are marked as completed should NOT show the overdue indicator, even if their due date is in the past.
4. **No Due Date**: Todos without a due date cannot be overdue and should not show any overdue indicator.
5. **Real-time Updates**: The overdue status should be calculated on the client side at render time, so it reflects the current date without requiring a page refresh.

### Non-Functional Requirements

1. **Performance**: Overdue calculation must be performed client-side with no additional API calls.
2. **Accessibility**: Overdue status must be communicated via both color and text (not color alone) to support color-blind users.
3. **Theme Support**: The overdue indicator must work correctly in both light and dark themes.
4. **Responsiveness**: The overdue indicator must display properly on all supported screen sizes.

## Acceptance Criteria

- [ ] A todo with a due date in the past and `completed = 0` displays an overdue indicator
- [ ] A todo with a due date in the past and `completed = 1` does NOT display an overdue indicator
- [ ] A todo with a due date today or in the future does NOT display an overdue indicator
- [ ] A todo with no due date does NOT display an overdue indicator
- [ ] The overdue indicator includes both a color change and a text label ("Overdue")
- [ ] The overdue styling is visible in both light and dark modes
- [ ] Tests cover all overdue detection edge cases

## Clarifications

### Visual Design

- **Indicator Style**: The overdue indicator will be a text badge ("Overdue") displayed next to the due date, styled with the danger color (red: `#c62828` in light mode, `#ef5350` in dark mode).
- **Card Border**: Overdue todo cards will have a left border accent in the danger color to provide an additional visual cue.
- **Due Date Text**: The due date text for overdue items will also be styled in the danger color.

### Behavioral Edge Cases

- **Midnight Boundary**: A todo is considered overdue when the current date (at midnight, start of day) is strictly after the due date. A todo due "today" is NOT overdue.
- **Timezone Handling**: Date comparison uses local date strings (YYYY-MM-DD format) compared to the local current date, avoiding timezone conversion issues.
- **Toggling Completion**: When a user marks an overdue todo as complete, the overdue indicator should immediately disappear. When unchecked, it should reappear.

### Interaction Patterns

- **No User Action Required**: The overdue indicator is purely informational - no additional user interaction is needed.
- **Edit Mode**: When a todo card is in edit mode, the overdue indicator is not displayed (the edit form takes over).
- **Sorting**: No change to sort order is required - overdue items maintain their creation date ordering.

### Data Handling

- **No Backend Changes**: The overdue logic is entirely client-side. No API or database changes are needed.
- **Date Format**: Due dates are stored as `YYYY-MM-DD` strings in the database and compared against `new Date().toISOString().split('T')[0]` for the current date.
