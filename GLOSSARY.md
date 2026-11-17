# Book Sync

A chatbot-agnostic prompt recipe that turns a chat session into a tool for readers who paused a book partway through and want to pick it back up without starting over.

## Language

**Reader**:
The person who started the book, stopped, and wants to continue it.
_Avoid_: User, customer

**Resume Point**:
The last chapter the Reader has fully read; reading continues at the start of the following chapter.
_Avoid_: Checkpoint, bookmark, cutoff

**Read Portion**:
Everything in the book from its start through the end of the Resume Point.
_Avoid_: Read part, past chapters

**Unread Portion**:
Everything in the book after the Resume Point.
_Avoid_: Future chapters, rest of the book

**Spoiler**:
Any information the Reader could not have learned from the Read Portion alone, including hints, foreshadowing, emphasis on what later proves important, and confirmations the book has not yet made.
_Avoid_: Leak

**Catch-up**:
The Markdown document the tool produces: a spoiler-free account of the Read Portion that lets the Reader continue from the Resume Point.
_Avoid_: Summary, recap, synopsis

**Chapter Reference**:
What the Reader types to identify the Resume Point: a chapter number or a chapter name.

**Book Text**:
The actual text of the book that the summary is built from, obtained (in order of preference) by the Reader uploading it, by the AI finding it in an online library, or by the Reader pasting it. Never the AI's own memory of the book.
_Avoid_: Source, file, memory

**Edition**:
A specific version of the book, such as a translation, whose chapter divisions may differ from other versions. The Resume Point is always defined in the Edition the Reader read.
_Avoid_: Version, copy
