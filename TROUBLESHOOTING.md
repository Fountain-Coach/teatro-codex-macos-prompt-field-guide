# Troubleshooting — Common macOS Prompting Pitfalls (Teatro)

Quick guidance for recurring issues when applying the language to macOS apps.

## Security-Scoped Bookmarks
- Start/Stop: Always call `startAccessingSecurityScopedResource` before use and `stopAccessing…` after.
- Stale bookmarks: Detect and re-prompt; replace the stored bookmark.
- Scope: Read vs read‑write differs; don’t assume write from prior access.

## Drag & Drop
- UTTypes: Mismatched UTType prevents drops; declare exactly what you accept.
- Async loading: `NSItemProvider` loads asynchronously; update UI state accordingly.
- Sandbox: Dropped file URLs still require security scope to persist access beyond the session.

## NSOpenPanel
- Allowed content: Restrict content types; otherwise users select unsupported files.
- Bookmark storage: Choose where to store (AppStorage/Keychain) and handle migration.
- Cancellation: Treat cancel as a normal branch; reset UI affordances.

## Multiwindow & Scenes
- Shared state: Provide a single shared model (EnvironmentObject/actor) to all scenes.
- Scene identity: Window(id:) helps target specific docs; avoid accidental duplicates.
- ScenePhase: React to background/foreground to pause timers and access.

## Menu Bar Apps
- Lifecycle: Dockless apps need explicit quit/restore paths; test menu focus.
- Windows: Opening windows from MenuBarExtra requires a stable handle.

## Accessibility
- Labels: Ensure interactive elements have accessibility labels/roles.
- Focus: Keyboard focus order must be predictable; test with VoiceOver.

## UI Tests
- Menus: Wait for menu building before selecting items in tests.
- Windows: Assert expected number of windows after actions; close between tests.

See also: [Glossary](GLOSSARY.md) · [Part 02 — Advanced Interaction](parts/part-02.md) · [System Interaction Example](examples/System-Interaction.score.teatro)
