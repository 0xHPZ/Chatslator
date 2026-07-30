# Translating Chatslator

Chatslator's interface is available in multiple languages, and community
contributions are always welcome. You can improve an existing translation or
help add a new one.

## What's open for contribution

**This repository does not contain Chatslator's source code.** It's a public
repository for downloads, release notes, and locale files.

The extension itself is built from a separate, private repository, so **only
the files inside [`locales/`](locales/) are open for community
contributions**. There isn't any application source code here to submit pull
requests against.

By opening a pull request that adds or edits a locale file, you agree that
your translation may be used, modified, and distributed as part of Chatslator.

If you'd rather not use GitHub, you can email a translation to
**zeerohpz@gmail.com** instead. See
[Submitting without GitHub](#submitting-without-github).

## How the language files work

Each language lives in its own file: `locales/<code>.json`.

The reference file is [`locales/en.json`](locales/en.json). Every other locale
automatically falls back to English for any missing strings, so **partial
translations are genuinely useful**. You don't need to translate the entire
file in one contribution.

Every translation is reviewed before being included in the extension, so
there's nothing to build or test locally. Just submit the JSON file.

Currently shipped locales:

| File | Language |
| --- | --- |
| `en.json` | English (source of truth) |
| `ja.json` | 日本語 |
| `fil.json` | Filipino |

## Step-by-step: editing an existing language

1. **Find the file.** Open [`locales/`](locales/) and select your language
   (for example, `fil.json` for Filipino).

2. **Edit it.** Click the pencil icon in GitHub to edit the file directly in
   your browser. **You don't need Git or any development tools.**

   Only translate the text on the right side of each entry.

   ```json
   // ✅ Correct
   "settings": "Configuración"

   // ❌ Incorrect
   "configuracion": "Configuración"
   ```

   **Never change the keys** (the text before the colon).

3. **Keep the file valid JSON.** Make sure every comma and quotation mark is
   still in the right place. See [Formatting rules](#formatting-rules) below.

4. **Open a pull request.** GitHub will guide you through creating a branch
   and opening a pull request after you click **Propose changes**. A simple
   title such as `Update Filipino translation` is perfect.

## Step-by-step: adding a new language

1. **Check it isn't already in progress.** Look through open issues and pull
   requests first so two people don't start the same translation.

2. **Copy `en.json`.** Duplicate `locales/en.json` and rename the copy using
   your language's code. See
   [Choosing a language code](#choosing-a-language-code).

3. **Translate every value.** Replace each English string with your
   translation while leaving every key exactly as it is.

4. **Open a pull request.** New languages also need to be registered inside
   the extension itself. That part isn't in this repository, so a maintainer
   will take care of it. A partial translation is still welcome.

## Formatting rules

Some parts of the files aren't ordinary text. Translating or removing them can
break the extension.

### Don't touch `$1`, `$2`, etc.

These are placeholders that Chatslator replaces at runtime with things like a
platform name, language name, or number.

You can move them wherever they sound natural in your language, but don't
change or remove them.

```json
// en.json
"resetOne": "Reset $1"

// fil.json
"resetOne": "I-reset ang $1"
```

```json
// en.json
"enable": {
  "title": "Translate $1 chat"
}

// ja.json
"enable": {
  "title": "$1 のチャットを翻訳"
}
```

### Plural forms use `"1"` and `"n"`

Some entries are objects instead of plain strings.

```json
"ctaJoin": {
  "1": "Join 1 person keeping Chatslator free for everyone.",
  "n": "Join $1 people keeping Chatslator free for everyone."
}
```

Translate both values while keeping the `"1"` and `"n"` keys unchanged. Use
whatever plural wording is natural for your language.

### Preserve formatting

If a translation contains line breaks (`\n`) or intentional spacing, keep
them unless there's a good reason to change them.

### Keep escaped characters

Some strings contain escaped characters such as `\"` or `\n`. Leave these as
they are unless you understand exactly what they're doing.

```json
"example": "Click \"Save\" to continue."
```

### One key, one piece of text

Each key represents one complete piece of text. Don't split one translation
across multiple keys or combine several keys into one.

### Match the tone, not just the words

Chatslator uses clear, conversational language. Avoid overly formal or
marketing-style translations, and prefer wording that feels natural to native
speakers.

### Keep placeholders and punctuation consistent

- Keep the same number of `$1`-style placeholders as the English source.
- Follow your language's punctuation and capitalization rules naturally.
- Don't remove placeholders or escaped characters.

### AI-assisted translations

You're welcome to use ChatGPT or other machine translation tools to help with
your translation. Please review the result before submitting to make sure it
sounds natural and matches the tone of the rest of the interface.

## Choosing a language code

Use the locale codes supported by Chrome and Firefox.

- Prefer a two-letter language code when possible (`es`, `de`, `ko`).
- Use `language_REGION` (underscore, **not** a hyphen) when the region
  matters, such as `pt_BR` or `zh_CN`.
- If you're unsure, check [Chrome's supported locales
  list](https://developer.chrome.com/docs/extensions/reference/api/i18n#locales) before naming your
  file. The filename **is** the locale code.

## Before submitting

Before opening a pull request or sending your translation by email, quickly
check that:

- The file is valid JSON.
- Every key from `en.json` is still present.
- You only translated the values, not the keys.
- `$1`, `$2`, and other placeholders are still present.
- Escaped characters such as `\n` and `\"` haven't been removed.
- The translation sounds natural to native speakers.

## Submitting without GitHub

If you don't have (or don't want) a GitHub account, you can still contribute.

Translate `en.json` (or edit an existing locale), save it as a `.json` file,
and email it to **zeerohpz@gmail.com**. Include which language it is and
whether it's a new translation or an update to an existing one.

## Questions

Open an issue, or email **zeerohpz@gmail.com**.