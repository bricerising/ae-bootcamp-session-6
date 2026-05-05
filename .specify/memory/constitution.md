# Project Constitution

## Overview

This constitution defines the governing principles and development guidelines for the Todo Application project. All AI-generated code and specifications must adhere to these principles to maintain consistency, quality, and alignment with the team's standards.

## Core Principles

### 1. Clean Code and Readability

Code must be readable, maintainable, and follow established conventions. Use camelCase for variables and functions, PascalCase for React components and classes, and UPPER_SNAKE_CASE for constants. Keep lines under 100 characters and use 2-space indentation throughout.

**Source**: [coding-guidelines.md](../../docs/coding-guidelines.md)

### 2. Single Responsibility

Every module, component, and function should have one well-defined responsibility. React components should focus on rendering and user interaction; services should handle API communication; utility functions should perform one operation well.

**Source**: [coding-guidelines.md](../../docs/coding-guidelines.md)

### 3. Test-Driven Quality

All new functionality must include tests. Target 80%+ code coverage. Tests should verify behavior, not implementation details. Use Jest with React Testing Library for frontend tests and Jest with Supertest for backend tests. Follow the Arrange-Act-Assert pattern.

**Source**: [testing-guidelines.md](../../docs/testing-guidelines.md)

### 4. Material Design with Halloween Theme

The UI follows Material Design principles with a Halloween-inspired color palette. Use orange (#ff6b35) as the primary color and purple (#9d4edd) as the accent. Support both light and dark modes. Follow the 8px spacing grid system. Cards have subtle shadows and 8px border radius.

**Source**: [ui-guidelines.md](../../docs/ui-guidelines.md)

### 5. Simplicity and Focus

The application is a single-user todo app focused on core CRUD operations. Avoid feature creep. No advanced filtering, search, bulk operations, or multi-user features. Keep the interface clean and minimal.

**Source**: [functional-requirements.md](../../docs/functional-requirements.md)

### 6. Monorepo Architecture

The project uses npm workspaces with a React frontend (packages/frontend) and Express.js backend (packages/backend). Frontend communicates with backend via REST API. The backend uses an in-memory SQLite database for persistence.

**Source**: [project-overview.md](../../docs/project-overview.md)

### 7. DRY and KISS

Don't repeat yourself - extract common code into shared utilities. Keep implementations simple and straightforward. Prefer readability over clever solutions. Write clear code first; optimize only when necessary.

**Source**: [coding-guidelines.md](../../docs/coding-guidelines.md)

### 8. Accessibility First

All interactive elements must be keyboard accessible. Use proper ARIA labels, maintain color contrast per WCAG AA standards, and ensure focus indicators are visible. Form labels must be associated with their inputs.

**Source**: [ui-guidelines.md](../../docs/ui-guidelines.md)

### 9. Error Handling

Handle errors gracefully with try-catch blocks. Provide meaningful, user-friendly error messages. Inform users when operations fail and offer recovery paths. Never expose internal error details to users.

**Source**: [coding-guidelines.md](../../docs/coding-guidelines.md)

### 10. Atomic Commits and Clear Messages

Each commit should represent one logical change with a descriptive commit message explaining "why". Use feature branches for new work and pull requests for code review before merging.

**Source**: [coding-guidelines.md](../../docs/coding-guidelines.md)

## Technology Stack

- **Frontend**: React 18, CSS (custom properties), Jest + React Testing Library
- **Backend**: Node.js, Express.js, better-sqlite3, Jest + Supertest
- **Build**: npm workspaces, react-scripts, nodemon
- **Style**: Material Design + Halloween theme, CSS custom properties for theming

## File Organization

### Frontend
```
packages/frontend/src/
  components/          # Reusable UI components
  services/            # API communication layer
  styles/              # Theme and global styles
  __tests__/           # Integration tests
```

### Backend
```
packages/backend/src/
  services/            # Business logic layer
  app.js               # Express configuration and routes
  index.js             # Server entry point
```

## Development Workflow

1. Create feature branch from main
2. Write specifications before implementation
3. Implement with tests alongside features
4. Run `npm test` to verify all tests pass
5. Run `npm start` to verify application works
6. Commit with descriptive messages
7. Create pull request for review
