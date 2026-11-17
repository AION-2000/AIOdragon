# Publish the AIOdragon game source

The game source is in **AIOdragon-GitHub-Ready-Source.zip**, not in the documentation-only checkout. The source kit contains the game engine, GLB assets, native Android project, tests, store artwork, and a full screenshot-enabled README. Signing secrets, generated binaries, and the unwanted watermark asset are excluded.

## Publish on Windows

1. Download and **extract** the complete source ZIP. Do not run it inside the archive.
2. Install Git for Windows and sign in to GitHub with an account that has write access to [AION-2000/AIOdragon](https://github.com/AION-2000/AIOdragon).
3. Open PowerShell in the extracted `AIOdragon` directory.
4. Run:

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -File .\scripts\publish-to-github.ps1
```

The script clones the existing repository into an **AIOdragon-github** sibling folder, copies the prepared source (without touching the original checkout's Git metadata), stages the files, creates a commit, and pushes to `main`. GitHub login may be required.

**Verify:** Open the repository and confirm `game/`, `android/`, `qa/`, `store/`, and `scripts/` appear.

## Security and licensing

Do not publish the separate private signing-backup ZIP or passwords. The reference game and original artwork are inherited from the supplied Skyfire project and may have redistribution restrictions. Confirm the right to publicly distribute those assets before pushing to a public repository; see `SOURCE-ATTRIBUTION.md`.
