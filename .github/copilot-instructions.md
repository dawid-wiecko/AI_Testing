# Copilot Instructions

This repository is a minimal test/demo repository. As it evolves, this file will document important context for AI assistants working in the codebase.

## Repository Overview

**copilot-cli-testing** is a test repository set up to validate Copilot CLI functionality and workflows. Currently minimal in scope, this file provides guidance for future development.

## Development Setup

### Prerequisites
- Git configured (author: dawid.wiecko@wp.pl)
- Standard development environment

### Environment Setup
Copilot's development environment is configured via `.github/workflows/copilot-setup-steps.yml`. This file is executed automatically before Copilot begins working on tasks. As the project evolves, uncomment and customize the language-specific setup steps (Node.js, Python, Java, .NET, Go, etc.) based on your tech stack.

### Running Tests, Builds, and Lints

As the project evolves and adds:
- **Test suites**: Document how to run tests (e.g., `npm test` for single test, `npm run test:all` for full suite)
- **Build commands**: Document the build process (e.g., `npm run build`, `make build`)
- **Linters**: Document linting commands (e.g., `npm run lint`, `npm run format`)

Currently: No automated tests, builds, or lints configured.

## Architecture

As the codebase grows, document here:
- High-level system design and component relationships
- Key architectural patterns or decisions
- Module boundaries and dependencies
- Data flow between major components

Currently: N/A for test repository.

## Code Conventions

As the codebase grows, document:
- File naming and organization conventions
- Code style expectations beyond linters
- Naming patterns (e.g., method prefixes, class naming)
- Common patterns or idioms specific to this codebase
- Configuration or environment-specific behaviors

Currently: No established conventions.

## Git Workflow

- Default branch: `main`
- Commits should include proper attribution
- When making commits via Copilot, use the standard commit message format with Co-authored-by trailer

## Adding to This File

When expanding this repository, update this file with:
1. **Build, test, and lint commands** - include how to run individual tests, not just full suites
2. **Architecture overview** - focus on context requiring multiple files to understand
3. **Project-specific conventions** - patterns not obvious from a single file
4. **Development workflows** - any special setup or deployment procedures

Do not include:
- Generic development practices (e.g., "write unit tests")
- Obvious instructions any developer would know
- Exhaustive directory listings
- Explanations of what isn't relevant

## Related Resources

- README.md: Project overview and purpose
