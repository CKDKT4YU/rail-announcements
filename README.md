# UK Railway Announcements

[View the website!](https://railannouncements.co.uk/)

A website to generate and play UK railway announcements.

> **Info**
>
> Due to a legal notice by Worldline IT Services UK Limited, Atos Anne's audio recordings are no longer available.
>
> For more information, please visit https://railannouncements.co.uk/atos-worldline

## Introduction

When Phil Sayer slowly begun leaving the railway, I wished I had gotten more recordings of his announcements. Because I didn't do that back then,
I decided I'll do it proactively this time!

## Contributing

> ⚠️ **Please follow these guidelines before submitting any files. If you don't, your PR may not be accepted.**

### Audio contributions

The folder for audio files can be found at `audio/`.

- Open a separate pull request for each announcement system you're modifying.
- Audio files should be split wherever possible, but don't overdo it.
- Audio files **must** be `mp3` files due to their [wide browser support](https://caniuse.com/mp3).
- **Files should be named based on the audio within them.** For example "We will be calling at" should be `we will be calling at.mp3`.
- Stations should be saved by their CRS code.
  - Some announcement systems use a high and low pitch version depending on whether they're at the start or end of a sentence, such as the Class
    700/707/717.
  - Don't know a CRS code? Use [http://national-rail-api.davwheat.dev/crs/<search term>](http://national-rail-api.davwheat.dev/crs/brighton), or
    the National Rail Journey Planner.
  - _For example, Brighton should be `BTN.mp3`._

### Running the website locally (simple Mac instructions)

These steps are written for a current macOS (tested November 2024) and assume only basic command-line knowledge.

#### 1) One-time prep

1. Install [Node.js 18 or newer](https://nodejs.org/en) (the standard macOS installer is fine).
2. Open Terminal and run:

   ```bash
   corepack enable
   ```

   This makes sure the repo’s bundled Yarn **4.3.1** is used automatically. You do **not** need to uninstall any other Yarn versions you may have tried.

#### 2) If you tried before and it failed

If a previous install attempt errored (for example, with a different Yarn version), clean the workspace before retrying:

```bash
rm -rf .yarn/cache node_modules .pnp.*
git checkout -- .
git clean -fd
```

#### 3) Install dependencies

From the repository root:

```bash
yarn install
```

#### 4) Start the app (three small servers)

Use three Terminal windows or tabs, all in the repo folder:

```bash
# Tab 1 – website
yarn run develop

# Tab 2 – API/worker proxy (wait for Tab 1 to say the site is ready first)
yarn run develop:workers

# Tab 3 – audio files
yarn run serve-audio
```

When all three are running, open [http://local.davw.network:8787](http://local.davw.network:8787). The custom hostname maps to localhost so audio and API calls work correctly during development.

#### 5) Do you need API keys?

No. The site’s live data requests hit the public `national-rail-api.davwheat.dev` endpoints, and local development uses the built-in Cloudflare Workers dev server with the bundled D1 database binding. You don’t need to supply any API keys or secrets for a local setup.

### Website contributions

This site is created with the React Framework using Gatsby. If you're not familiar with React or Gatsby, you may want to research them before
contributing.

**Before committing your changes, format your code:**

```bash
yarn run format
```
