# Tasks: Overdue Todo Items Implementation

## Task 1: Add Overdue Color Variables to Theme

**File**: `packages/frontend/src/styles/theme.css`
**Action**: Add `--overdue-color` custom property to both `[data-theme="light"]` and `[data-theme="dark"]` selectors.

- Light mode: `--overdue-color: #c62828`
- Dark mode: `--overdue-color: #ef5350`

## Task 2: Add Overdue CSS Styles

**File**: `packages/frontend/src/App.css`
**Action**: Add CSS rules for overdue todo cards.

- `.todo-card.overdue` - left border accent with overdue color
- `.todo-card.overdue .todo-due-date` - text color set to overdue color
- `.overdue-badge` - styled text badge (font-size: 11px, font-weight: 600, padding, border-radius, background/color using overdue-color)

## Task 3: Implement Overdue Logic in TodoCard Component

**File**: `packages/frontend/src/components/TodoCard.js`
**Action**: Add overdue detection and rendering.

- Add `isOverdue` helper function that checks: `dueDate` exists AND `completed` is falsy AND `dueDate < today`
- Add `overdue` class to the card's className when isOverdue returns true
- Render an "Overdue" badge span next to the due date when overdue

## Task 4: Write Tests for Overdue Behavior

**File**: `packages/frontend/src/components/__tests__/TodoCard.test.js`
**Action**: Add test cases for overdue indicator.

- Test: overdue indicator shown for past due date and incomplete todo
- Test: overdue indicator NOT shown for past due date and completed todo
- Test: overdue indicator NOT shown for future due date
- Test: overdue indicator NOT shown when no due date set
- Test: overdue CSS class applied correctly
- Test: "Overdue" text is present in the DOM for overdue todos

## Task 5: Verify All Tests Pass

**Action**: Run `npm test` to verify existing and new tests all pass without regressions.

## Task 6: Manual Verification

**Action**: Run `npm start` and visually verify:
- Create a todo with a past due date → overdue indicator appears
- Mark it complete → overdue indicator disappears
- Create a todo with a future due date → no overdue indicator
- Toggle between light/dark modes → overdue styling works in both
