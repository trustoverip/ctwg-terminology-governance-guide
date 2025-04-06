# How to split `terms_and_definitions.md` file into multiple files

Find the most recent info about the working and user manual here: [Splitter-tool](https://trustoverip.github.io/spec-up-t-website/docs/advanced-features/splitter)

## General info

At the time of writing the Governance Guide (2024)

Note:

- The JSON file `specs.unsplit.json` is a one time back-up of `specs.json`.
- When running the script below (`npm run split`) the JSON file `specs.unsplit.json` will be copied to `specs.json`. **Use this file to change the config since this is the source**.
- Make sure that at the end this entry **"account":"trustoverip"** is correctly set.
- The `spec.json file will have multiple new entries, one entry per defined term. The file can grow large.
- The file is written without newlines. If you want to make it readable, run a code beautifier.

## How to split terms_and_definitions.md

Split `terms_and_definitions.md` into multiple files, one file per term:

```
npx spec-up-splitter [pathToTermsFile] [pathToTermsDir]
```

Create the glossary file (named `index.html`):

```
npm run render
```
or option 1 of the menu

```
npm run menu
1
```
