# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a VS Code extension providing XML Property List (plist) syntax highlighting.

## Development

This is a declarative, configuration-only extension with no compilation step. There are no build, test, or lint scripts.

**To debug/run the extension:**
- Open this folder in VS Code
- Press `F5` to launch the Extension Development Host (configured in `.vscode/launch.json`)

**To package the extension:**
```bash
npx vsce package
```

## Architecture

The extension uses **TextMate grammar injection** — it overlays plist-specific scopes onto the existing XML language rather than defining a standalone language. The injection selector `L:text.xml` in `syntaxes/property-list-xml.json` is the key mechanism.

Detection of plist files relies on a `lineMatch` pattern in the grammar that matches files beginning with `<?xml` followed by `<!DOCTYPE plist`.

**Key files:**
- `syntaxes/property-list-xml.json` — Main grammar; defines all TextMate scope patterns for plist elements
- `package.json` — Extension manifest; declares the grammar contribution and snippet contribution (both targeting `language: xml`)
- `snippets/snippets.code-snippets` — Code snippets for plist tags
