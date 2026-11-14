---
name: courier
description: Prepare a copy of a note for delivery to another vault or person without editing either source vault.
---

# courier

Prepare a user-approved note copy for transfer. This skill does not send files or write into another vault unless an authorized tool and explicit destination permission are available.

## Steps
1. Ask for the source note, recipient or destination, and whether to preserve links, sanitize, or collate. Use `sanitize` or `collator` when relevant and available.
2. Verify destination access. Never infer permission to share private or third-party information.
3. Preserve content and links unless the user requests changes. Do not claim that wiki-links resolve in the destination without checking.
4. Save the transfer-ready copy under `<source vault>/AI System/Courier/`; do not edit the source or destination vault.
5. Report the copy path, unresolved links, and any approval needed before delivery.
