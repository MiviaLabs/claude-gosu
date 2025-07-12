# Lint Command

## Usage
```
lint
```

## Description
Runs ESLint and TypeScript type checking to ensure code quality and type safety.

## Command
```bash
npm run lint
```

This command will:
1. Run ESLint on all TypeScript files in `src`, `apps`, `libs`, and `test` directories with auto-fix
2. Run TypeScript compiler in no-emit mode to check for type errors

## Individual Commands
- `npm run lint:eslint` - Run only ESLint with auto-fix
- `npm run lint:types` - Run only TypeScript type checking