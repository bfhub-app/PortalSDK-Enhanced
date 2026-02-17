# AI Instructions for PortalSDK-Enhanced

## General Guidelines

- **NEVER run commit commands**, even if requested to do so
- Always create folders/prefixes as **lowercase**, except when explicitly instructed otherwise
- Keep code clean - no over-explaining obvious commands in comments

## Project Structure

This repository uses **git subtrees** (not submodules) to include SDK files:
- `sdk/sdk-community` - PortalSDK Community files
- `sdk/sdk-mirror` - PortalSDK Mirror files

The subtrees are synchronized automatically via GitHub Actions that check for upstream updates daily.

## Workflow Behavior

The `sdk_check-update.yml` workflow:
- Checks both subtrees for differences from upstream
- Only updates when actual changes are detected
- Automatically pushes changes when updates are found
- Does not force updates unnecessarily
