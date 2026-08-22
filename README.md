# Cookin Project

Welcome to the Cookin monorepo! This workspace is set up for collaborative development using VS Code Live Share.

## Collaboration Setup

1. **Host (MacBook):** Open this folder in VS Code, ensure the Live Share extension is installed, and start a Live Share session from the sidebar or status bar.
2. **Guest (iPad/Mobile):** Click the Live Share link provided by the host to join via the browser or compatible app.

## Project Structure

This repository uses [npm workspaces](https://docs.npmjs.com/cli/using-npm/workspaces) (or your preferred package manager). 

- `apps/`: Contains the main applications (e.g., `mobile`, `supabase`).
- `packages/`: Contains shared libraries, UI components, and API configurations (e.g., `api`, `config`, `ui`).

## Getting Started

1. Make sure to install dependencies in the root (once you add some apps):
   ```bash
   npm install
   ```
2. Any environment variables (`.env` files) are excluded from Live Share to keep secrets safe. The host will need to configure those locally.

Happy coding!
