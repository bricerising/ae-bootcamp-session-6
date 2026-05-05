# Implementation Plan: Overdue Todo Items

## High-Level Approach

The overdue indicator feature is a purely frontend enhancement. We will add an `isOverdue` utility function, integrate it into the `TodoCard` component, add appropriate CSS styles for both themes, and write comprehensive tests.

## Architecture Decisions

1. **Client-Side Only**: No backend changes required. The overdue calculation happens at render time in the frontend.
2. **Utility Function**: Create a reusable `isOverdue(dueDate, completed)` helper to keep the logic testable and separate from presentation.
3. **CSS Classes**: Use a `.overdue` CSS class on the todo card to drive styling, following the existing pattern of `.completed`.
4. **Theme Variables**: Add CSS custom properties for overdue colors in both light and dark themes.

## Files to Modify

### Frontend Changes

| File | Change Type | Description |
|------|-------------|-------------|
| `packages/frontend/src/components/TodoCard.js` | Modify | Add overdue detection logic and render overdue indicator |
| `packages/frontend/src/App.css` | Modify | Add overdue styling rules |
| `packages/frontend/src/styles/theme.css` | Modify | Add overdue color variables for both themes |
| `packages/frontend/src/components/__tests__/TodoCard.test.js` | Modify | Add tests for overdue indicator behavior |

### No Backend Changes

The backend already stores and returns `dueDate` and `completed` fields. No API changes are needed.

## Component Modifications

### TodoCard Component

- Import or define an `isOverdue` helper function
- Calculate overdue status: `dueDate` is before today AND `completed` is falsy
- Add `overdue` CSS class to the card wrapper when overdue
- Render an "Overdue" badge element next to the due date when overdue
- Ensure the overdue indicator is hidden when in edit mode or when completed

### CSS / Theme Updates

- Add `--overdue-color` CSS custom property to both light and dark theme definitions
- Add `.todo-card.overdue` styles with left border accent
- Add `.overdue-badge` styles for the text indicator
- Add `.todo-card.overdue .todo-due-date` color override

## Integration Points

- The overdue logic integrates at the `TodoCard` component level only
- No changes to props interfaces (`TodoList` and `App` pass the same data)
- The existing `todo.dueDate` and `todo.completed` fields provide all data needed

## Risk Assessment

- **Low Risk**: This is an additive change with no modifications to data flow or API
- **Date Edge Cases**: Mitigated by using simple string comparison of YYYY-MM-DD format dates
- **Theme Compatibility**: Mitigated by using CSS custom properties consistent with existing patterns
