# Testing the prompt

Manual checks. Run them on each platform after changing `prompt.md`: NotebookLM (Gemini Notebook), ChatGPT, Claude, Gemini, Grok.

## Length

`prompt.md` must stay under 8,000 characters (see `docs/adr/0002-first-message-prompt-under-8k.md`):

```sh
test "$(wc -m < prompt.md)" -lt 8000 && echo OK || echo "TOO LONG"
```

## Test book

**_Strange Case of Dr Jekyll and Mr Hyde_** (Stevenson, public domain, [Project Gutenberg #43](https://www.gutenberg.org/ebooks/43)). It is short, the model knows the twist, and the last chapters' titles give it away ("Dr. Lanyon's Narrative", "Henry Jekyll's Full Statement of the Case").

Resume Point for the spoiler checks: **chapter 7, "Incident at the Window"**.

## Checklist

### Setup
- [ ] Greets, then asks one question per message.
- [ ] Recommends uploading, with the right format advice for this platform (e.g. EPUB → PDF/TXT on ChatGPT).
- [ ] Declining the upload: offers online search only if the platform can search, and offers pasting.
- [ ] Asking for a Catch-up "from memory": refuses and offers the options again.
- [ ] Online search uses a full-text library (e.g. Gutenberg), not a summary site.
- [ ] Confirms title, author and Edition.
- [ ] Ambiguous Chapter Reference (e.g. "the incident one", which matches chapters 5 and 7): lists the matches by position only ("Chapter 5 or Chapter 7?"), with no titles and no table of contents.
- [ ] "I'm halfway through chapter 5": asks for the last chapter finished completely.
- [ ] Ask to search online while writing in Spanish: looks for a Spanish Edition first, and asks before falling back to another language.
- [ ] Edition differs from the Reader's (e.g. found online): shows the matched chapter's title and asks for confirmation.
- [ ] Offers Quick / Standard / Detailed, and Quick fits in about one page.
- [ ] Upload only the first half of the book and ask for chapter 8: says the text is cut off and asks for the rest.
- [ ] Writing in a language other than the book's: asks which language the Catch-up should be in.

### Catch-up (Resume Point: chapter 7)
- [ ] Header has title, author, Edition, Book Text origin, date (if known), and "continue with the next chapter".
- [ ] Does **not** state or hint that Jekyll and Hyde are the same person.
- [ ] Does **not** show the titles of chapters 8–10.
- [ ] No foreshadowing ("this will matter", "little does he know", ...).
- [ ] Hyde's hold over Jekyll and the will stay open questions under **Open threads**.
- [ ] Lanyon's shock (chapter 6) stays unexplained.
- [ ] "Right before you continue" ends at the window scene, not later.
- [ ] Offered as a downloadable `.md` where the platform can create files; otherwise explains how to save it.

### Follow-ups
- [ ] "Who is Mr. Utterson?" answered from chapters 1–7 only.
- [ ] "Is Hyde actually Jekyll?" gets the fixed reply ("That isn't covered in what you've read so far."), with nothing added.
- [ ] "Is Hyde actually Utterson?" (a wrong guess) gets exactly the same reply.
- [ ] "What happens in the next chapter?" declined.
- [ ] "I've now read chapter 8 too": the Resume Point does not move; suggests a new chat.
