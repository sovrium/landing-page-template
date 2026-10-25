# Tablée — a landing page

> A bilingual product landing page with a demo request the owner reads in the admin.

Built with [Sovrium](https://sovrium.com) — a configuration-as-code interpreter: one config
file in, a complete self-hosted web application out.

## Use this template

Click **Use this template** on GitHub to copy this app into your own repository (clean
history, yours to modify), or scaffold it locally:

```bash
curl -fsSL https://sovrium.com/install | sh
sovrium init my-landing-page --template landing-page
```

## What's inside

The landing page of Tablée, a fictional booking product for independent restaurants, at
`/en/` and `/fr/`: one sentence about what it does, the product itself (Friday's dinner as
it shows it), three things it does, three steps to start, and a demo request. The French
page is written in French, and the language switcher keeps the reader's place. The page
claims no figure it cannot prove.

A request lands in the `demo_requests` table, which only the owner reads, in the admin at
`/_admin`. Nobody can open an account; the owner comes from `AUTH_ADMIN_EMAIL` and
`AUTH_ADMIN_PASSWORD`. Each language shares with its own PNG card (`public/og-en.png`,
`public/og-fr.png`); the site follows the system's light or dark scheme.

Optional: each request also becomes a lead in your Pipedrive. It is the
`form-to-pipedrive-lead` recipe from the Sovrium library (`sovrium library add
recipe/form-to-pipedrive-lead`); set `PIPEDRIVE_API_TOKEN` to turn it on — without it the app
runs exactly the same.

Everything is declared in [`app.yaml`](./app.yaml) and the [`config/`](./config) tree — no
application code. The words are in `config/languages.yaml`; rename the product there.

## Run locally

```bash
curl -fsSL https://sovrium.com/install | sh
cp .env.example .env
sovrium start app.yaml --watch
```

Zero-config: embedded SQLite, local file storage, no variable required to boot.
[`.env.example`](./.env.example) lists the optional ones this app reads.
The first administrator comes from `AUTH_ADMIN_EMAIL` and `AUTH_ADMIN_PASSWORD` on the
first start, or from `sovrium admin create <email>`.
`--watch` reloads the app each time you save a config file.

## Deploy

Ship it to Sovrium Cloud from this directory: sign in once, then deploy. The CLI finds or
creates the app it deploys to, checks the variables it needs, bundles and uploads it, and
ends only once the app answers at its address.

```bash
sovrium login
sovrium deploy
```

Any other host works the same way: run the `sovrium` binary with this config (see the
[deployment guides](https://sovrium.com/en/docs/installation)).

## About this repository

This repository is **auto-published from the
[Sovrium monorepo](https://github.com/sovrium/sovrium)** on every release
(source: [`src/templates/landing-page`](https://github.com/sovrium/sovrium/tree/main/src/templates/landing-page)).
Issues are welcome here; please send code contributions upstream to the monorepo so the
template stays in sync with the engine. The pinned engine release lives in
`.sovrium-version`.

License: [MIT](./LICENSE). The Sovrium engine itself is licensed separately
([BSL 1.1](https://github.com/sovrium/sovrium/blob/main/LICENSE.md)).
