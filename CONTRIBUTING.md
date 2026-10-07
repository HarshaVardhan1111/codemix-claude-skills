# Contributing

Thank you for helping. You do not need to be a programmer. You can edit files on the GitHub website.

## Add a glossary word or fix a wrong meaning

The Tanglish word list is in [`tanglish-to-english/references/glossary.md`](tanglish-to-english/references/glossary.md).

1. Open the file on GitHub.
2. Click the pencil icon (Edit).
3. Add your word to the right table, or fix the meaning.
4. Click **Commit changes** and choose **Create a new branch and start a pull request**.
5. In the pull request, write:
   - the word,
   - its meaning,
   - one real example sentence,
   - other spellings people use.

### Example

You notice "kitta" is missing. You add one row to the **Grammar endings** table:

```markdown
| kitta | to / with (a person) (owner kitta sollu = tell the owner) |
```

Your pull request text:

> **Add "kitta"**
>
> Meaning: to / with a person.
> Example: "manager kitta kelunga" = "please ask the manager".
> Other spellings: kitte, kita.

### Simple rules

- One topic per pull request.
- If you fix a meaning, say why the old one is wrong.
- Spelling varies. Add common spellings with `/` (for example `venum / vendum`).
- Do not add rude words or names of real people.

## Add a new language skill

Example: you want to add Hinglish.

1. **Copy the folder.** Copy `tanglish-to-english/` and rename it, for example `hinglish-to-english/`. Keep the same structure:

   ```
   hinglish-to-english/
   ├── SKILL.md
   └── references/glossary.md
   ```

2. **Edit `SKILL.md`.**
   - Change `name:` to the new folder name (`hinglish-to-english`).
   - Rewrite `description:` for the new language. Include a real example sentence.
   - Replace the examples with ones in the new language.
   - Keep the same writing rules: keep the meaning, never add facts, use placeholders.

3. **Write its own glossary.** Put common words, grammar endings and address words in `references/glossary.md`. Do not copy Tamil words.

4. **Write its own evals file.** Create `evals/hinglish-to-english.md`. Add at least 12 tests. Cover the same kinds of tests as [`evals/tanglish-to-english.md`](evals/tanglish-to-english.md): leave request, client delay, HR request, ticket follow-up, friend message, native script mixed with English, very short input, an ambiguous word, and missing names or dates.

5. **Add a row to the README skills table.**

   ```markdown
   | [hinglish-to-english](hinglish-to-english/) | Hindi + English | Available |
   ```

6. **Test it.** Run every test in your evals file. Fix the skill until they pass.

7. **Open a pull request.**

## Package a skill (for maintainers)

The `.skill` file is a ZIP file with the skill folder at the top level. From the repo root:

```bash
zip -r tanglish-to-english.skill tanglish-to-english
```

Attach the file to a GitHub release. Do not commit `.skill` files.
