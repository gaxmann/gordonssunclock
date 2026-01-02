# Gordon's Sun Clock - Translation Guide

## Language Files

The German language file (`de.json`) is the **original source language**. English serves as the fallback language and will be used whenever a language or translation entry is missing.

---

## Types of Language Support

Sun Clock distinguishes between three levels of translation completeness. These levels describe how much of the application interface is translated and which parts fall back to English.

### Fully translated languages

Fully translated languages contain translations for **all entries** in the language file. Currently, these include: *English (en), Deutsch (de), Español (es), Français (fr), Русский (ru), and 中文 (zh).* 

My long-term goal is to provide full support only for the most widely used languages (roughly the global top ten: ✓English, ✓Simplified Chinese, ✓Spanish, Hindi, Arabic, ✓French, Bengali, Portuguese, ✓Russian, Indonesian, ✓German). Maintaining a larger number of fully translated languages would create more ongoing work than I can realistically support. Full translations require significant effort, not only for the initial translation but also for ongoing maintenance as new features and content are added.

---

### Partially translated languages

Partially translated languages typically include all entries **up to and including** the `"txlegende"` key in the language file.

This covers:
- the complete settings page (labels, buttons, explanations)
- the data overview page (legend and explanations)

The following sections fall back to English:
- the tutorial page (“How to read the dial”)
- the About page

---

### Minimally translated languages

Minimally translated languages provide **at least** all labels required for the settings interface. Technically, this corresponds to all entries up to and including `"txpartsupport"`, plus the small `"txlegende"` entry.

This level ensures basic usability while keeping translation effort minimal.

---

## Translation Guidelines

When translating, please **keep all control codes unchanged**:

- `[XXXXXX]` and `{xxxxxx}` are variables that will be replaced by the programme
- `[~LF]` represents linefeeds (like `\n`). You can replace them with actual linefeeds if needed. `[NDASH]` is the en dash character (long hyphen) and could be replaced (if you want to)
- `[DF]` and `[SP]` are control codes for design layout (keep them, don't change them)

---

## Dictionary Entries


### Meta data
In the `"_meta"` entry, you will find the version number and date of the file/translation. As long as the minor version number is the same, only the texts of the translations have been changed. If the minor version number is different, there are (also) new or changed keys. 

### Quotation Marks
The `"quotes"` entry defines the local quotation marks used in your language, e.g.: 
- „Hello“ (German), «Hello» (French), ‘Hello’ (English)

### Shorts for hours and days
The (a) `"hoursh"` entry is the short form for hours (e.g. `24h`). (b) `"daysh"` is the short form for days (e.g. `in 4d`). (c) `"oclocksh"` is the short form for times without seconds, for example `12:35h` (you can leave the latter one empty if only `12:35` used in your language). 

---

### Plural Rules for ’Day(s)’

Most languages use different words for ’day’ depending on the number (e.g. 1 day, 2 day**s**). The entry `"xxdays"` defines these forms. (Use `%` where the number should appear.)

#### Examples

**English**
```json
    "xxdays": {
        "1": "% day",
        "*": "% days"
    },
```
**Russian**
```json
    "xxdays": {
        "1": "% день",
        "2-4": "% дня",
        ".":   "% дня",
        "*":   "% дней"
    },
```

#### Key Meanings
- `"1"` → applies when the number is exactly 1 (e.g., `1` → `% day`)
- `"2-4"` → applies for whole numbers from 2 to 4 inclusive (e.g., `2`, `3`, `4`)
- `"."` → applies to decimal numbers (e.g., `1.5`, `2.7`)
- `"*"` → fallback for all other cases **(mandatory!)**

### Short Form of Ordinal Numbers

The same rules are used for `"oridinalsh"`, which defines the short form of ordinal numbers (such as ’3.’ or ’3rd’). Additionally: if your language distinguishes grammatical gender, you can specify gendered endings in the order masculine/feminine/neuter, separated by slashes, for example in Russian: %-й/%-я/%-е. (If your language has only two genders or only one, simply provide the corresponding forms.) E.g. (Use % where the number should appear.)

**French**
```json
    "ordinalsh": {
        "1": "%er/%re",
        "*": "%e"
    },
```
**German**
```json
    "ordinalsh": {
        "*": "%."
    },
```
---

### Word Separation Rules

The language dictionary contains entries to help with correct word separation in your language. If you're unsure what to enter, leave them empty `[]`.

Example entries:

```json
    "char_vowels": "aeiouyäöüáéíóúÄÖÜÁÉÍÓÚ",
    "char_consonants": "bcdfghjklmnpqrstvwxyzñÑ",
    "char_splitafter": ".,;:!?“‘”-—)]}%&*+=/\\|>@#_×÷≈≠≤≥°¶•…”’»`",
    "char_splitbefore": "„‚([{<$~^€£¥±©®™§†‡“”‘«¿¡",
    "graph_dontseparatebetween": [
        "sch",
        "ch",
        "ck",
        "tz",
        "pf",
        "qu",
    ],
    "graph_dontseparatebefore": [
        "nd",
        "hn",
        "rn",
        "rg",
        "nb",
        "sz",
        "sw",
        "rd",
        "lg",
        "nü",
    ],
    "graph_dontseparateafter": [
        "nb"
    ],
    "graph_separateafter": [],
```

---

## Contributing

Translations and corrections are welcome, provided that the technical structure of the language files is respected.

### New translations

To create a new translation, start from an existing file, preferably `de.json` (original source language) or `en.json`. Rename the file to the appropriate language (e.g. hindi.json) and translate the string values while keeping all keys and control codes unchanged. Pay particular attention to the control codes used for layout, variables, and formatting.

Completed translations can be submitted via pull request or by email (see the last page of the app).

### Corrections and partial contributions

To improve an existing translation, copy the corresponding language file and keep **only the entries you intend to change**. Remove all other entries. This makes review and merging significantly easier.

Corrections can be submitted via pull request or by email.

### Notes

- Never modify or remove control codes such as `[~LF]`, `{xxxx}`, `[DF]`, `[SP]`, or formatting tags.
- Partial contributions should contain only modified entries.
- Try to preserve the original tone and terminology of the existing translation.

Thank you for helping make Gordon's Sun Clock accessible to more people!
