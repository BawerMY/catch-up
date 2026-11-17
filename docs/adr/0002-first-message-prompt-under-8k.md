# One prompt, pasted as the first message, kept under 8,000 characters

The recipe is a single self-contained prompt, pasted as the first chat message, with platform facts built in. It is not a short core for custom-instruction slots plus separate versions per platform. It must stay under 8,000 characters:
- ChatGPT turns first messages over 10k characters into attachments.
- NotebookLM's chat configuration reportedly allows about 10k characters.

ChatGPT's custom instructions (1.5k or 5k characters) are too small for it, which is why the first message, not a custom-instruction slot, is the official way to use it.

## Consequences

Any new feature has to fit the character budget. Platform guidance stays as compact facts, not step-by-step guides.
