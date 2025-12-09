# AGENTS.md - AI Agent Guidelines

## Project Overview

See the [README](./README.md).

## Tech Stack & Architecture

### Current Setup

- **Package Manager**: bun
- **Linting**: ESLint + Prettier

## File Organization Guidelines

When creating new files, follow this structure:

```
src/
├── feature/  # Each feature within a subdirectory here
├── types/    # TypeScript type definitions
├── data/     # Constants and other fixed data
├── utils/    # Common utility functions
```

## Development Standards

### Documentation Style

**Always use JSDoc comments** for code documentation:

```typescript
/**
 * Brief description of the interface/type/function
 *
 * @example
 * const example: LocationData = {
 *   habitat: ['deciduous-forest'],
 *   substrate: 'wood'
 * }
 */
export interface LocationData {
  /** Array of habitat types where the mushroom was found */
  habitat: string[]
  /** Optional substrate information (e.g., wood, soil, grass) */
  substrate?: string
}

/**
 * Calculate confidence score for a mushroom species match
 *
 * @param userData - The user's collected mushroom observations
 * @param species - The mushroom species to compare against
 * @returns Object containing the match score (0-100) and matched features
 */
export const calculateMatchScore = (
  userData: MushroomData,
  species: MushroomSpecies,
): { score: number; matchedFeatures: string[] } => {
  // Implementation...
}
```

Do not comment with numbered bullets.

### TypeScript Requirements

- Use TypeScript strictly - **NO `any` types**
- Write descriptive component and function names
- **Prefer JSDoc comments** for all interfaces, types, functions, and components
- Use multi-line JSDoc format with `/**` and `*/` delimiters
- Include parameter descriptions and return types in JSDoc comments
- Follow best practices (hooks, component composition)

### Code Quality

- Use ESLint and Prettier consistently
- **Document all code with JSDoc comments** - interfaces, types, components, and functions should have clear documentation
- Write unit tests for utility functions
- Test builds with `bun build` to ensure production readiness
- Use `utils/logger` to log using `pino`. Use logs liberally
- For long and complex tasks, log the progress

## Development Workflow

### Available Commands

- `bun dev` - Start development server
- `bun build` - Build for production
- `bun preview` - Preview production build
- `bun lint .` - Run ESLint
- `bun lint:fix .` - Run ESLint with auto-fix
- `bun format .` - Format code with Prettier
- `bun format:check .` - Check code formatting
- `bun type-check` - Run TypeScript type checking

### Git Workflow

- Make atomic commits with small but complete changes
- Use lefthook for pre-commit hooks
- Follow conventional commit messages
- Ensure all code passes linting and type checking
- Write meaningful commit messages

## Future Considerations

### Planned Features

TODO

## Agent-Specific Instructions

### When Working on This Project

- **Follow the established patterns** - Use the provided interfaces and hooks
- **Test thoroughly** - Run `bun build` to ensure code compiles without errors
- **Document everything** - Use JSDoc comments for all interfaces, types, components, and functions (not just complex ones)
- **Maintain consistency** - Follow the established naming conventions and file structure

### Code Review Checklist

- [ ] TypeScript types are properly defined (no `any`)
- [ ] All interfaces, types, components, and functions have JSDoc comments
- [ ] Appropriate logs are included
- [ ] Code follows established patterns
- [ ] Tests are included for new functionality
- [ ] Linting passes without errors
- [ ] `bun build` completes successfully
