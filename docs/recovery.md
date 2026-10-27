# Source recovery

## Current state

This checkout preserves an incomplete Create React App snapshot. `package.json`
declares React 19, TypeScript 4.9, `react-scripts` 5.0.1, Google's generative AI
SDK, and testing dependencies. These declarations do not establish that the
documented application ever ran from this repository.

The HTML template mounts an empty `root` element and references the supplied
icons and manifest through `%PUBLIC_URL%`. Those six static files have been moved
unchanged into `public/`, the layout described by the template itself. The
default React branding remains intact. Package manifests and TypeScript settings
are unchanged; `tsconfig.json` still includes `src`.

Missing material includes the entire `src/` directory: the entry point, the
`src/App.tsx` mentioned in the original README, any components, styles, speech
handling, provider integration, speaker profiles, and tests. No implementation
or results have been reconstructed from the feature descriptions.

## Search evidence — 2026-10-27

The initial checkout was clean on `cleanup/organization-20261027` at
`214220e11e37a4da4ed95921ce61640e6fbc1dca`.

| Search | Result |
| --- | --- |
| `git rev-parse --is-shallow-repository` | `false`; the local history is not shallow |
| `git log --all --format=fuller --stat` | Two commits, both dated 2025-04-18 |
| `git log --all --name-only --format= \| sort -u` | Only the ten original root files; no application source |
| `git reflog --all` | Clone and cleanup-branch setup only |
| `git fsck --full --no-reflogs` | Exit 0 with no output; no dangling recovery candidates reported |
| `git ls-remote --heads --tags origin` | Only `refs/heads/main`, at the same `214220e…` commit; no tags |

The first commit, `9fc73e5c42e933db643b8bbe5c0d3f444bdc51d2`, introduced
`README.md`, `package.json`, `package-lock.json`, and `tsconfig.json`. The second,
`214220e11e37a4da4ed95921ce61640e6fbc1dca`, added `index.html`, `manifest.json`,
`robots.txt`, `favicon.ico`, `logo192.png`, and `logo512.png` at the root.

Bounded local searches found only this checkout:

- Case-insensitive path-name searches for `auratracker`, `aura-tracker`, and
  `aura_tracker` under `/Users/main/Desktop`, `/Users/main/Documents`,
  `/Users/main/Downloads`, and `/Users/main/.t3/worktrees`, at `find -maxdepth 4`,
  pruning `.git`, `node_modules`, `.next`, and `.cache`.
- Package-name inspection under `/Users/main/Desktop/coding`,
  `/Users/main/Documents`, and `/Users/main/Downloads`, through four directory
  levels below each root. Of 28 `package.json` files inspected, only this
  checkout declared an AuraTracker package name. Dependency, cache, virtual
  environment, and hidden directories were excluded.

These searches do not rule out renamed projects, deeper directories, archives
with unrelated names, deleted files, external disks, other machines, or backups.
No source was recovered, and no other repository was modified.

## Restore from an authentic copy

1. Obtain the original source from the author, a verified Git ref, an old working
   copy, or a backup. Record its origin and revision before copying it here.
   A description of the app is insufficient to recover its behavior.
2. Inspect that copy for credentials and private data. Keep real keys out of Git
   and browser-delivered code. The original README's suggestion to embed an
   ElevenLabs key in `src/App.tsx` is unsafe and has been withdrawn. Client
   environment variables do not keep provider keys secret. An authenticated
   server-side integration would need to be supplied and verified; none exists
   in this snapshot.
3. Restore the complete `src/` tree and any additional authentic assets or
   configuration. Compare its dependency requirements with the preserved
   manifests; do not replace the lockfile or invent an entry point just to make
   a build pass.
4. With source restored and a compatible Node/npm toolchain established, the
   preserved scripts describe this intended workflow:

   ```sh
   npm ci
   npm start
   # Separately, validate the recovered source:
   npm run build
   npm test -- --watchAll=false
   ```

   The original README directs users to `http://localhost:3000`. These commands
   have not been validated against recovered source. Recover authentic tests
   before interpreting test results. Follow the repository/workstation runner
   guidance before heavy installation, build, or test work.
5. Verify microphone permissions, speech behavior, speaker training, history,
   chat, and optional voice responses against the recovered implementation.
   The [historical notes](historical-project-notes.md) are a comparison aid, not
   proof that those features exist or work.

## Cleanup verification

Lightweight checks cover JSON parsing, manifest/lockfile dependency agreement,
local documentation links, public asset references, byte-for-byte preservation
of the six moved files, and whitespace errors. Application installation, builds,
and tests are blocked by absent source and were not run. No dependency versions
were changed.
