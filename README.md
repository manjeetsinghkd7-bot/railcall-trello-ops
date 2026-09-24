# RailCall Trello Operations

A governance-first Trello integration for RailCall that provides 10 practical Trello operations for AI-driven task and project workflows. External write actions are handled through RailCall's governed execution flow.

**Marketplace Listing:**

https://railcall.ai/marketplace/manjeet-singh-2/trello-ops

# Who It's For

This module is for teams and developers using RailCall to automate Trello-based task and project workflows, including card creation, updates, movement between lists, comments, members, labels, searching, and board-level card retrieval.

# Features

The module provides 10 commands:

- Create a card
- Get a card
- Update a card
- Move a card between lists
- Add a comment
- Assign a member
- Add a label
- Remove a label
- Search cards
- List cards on a board

# Installation

Install the published module from the RailCall Marketplace:

```bash
railcall market install manjeet-singh-2/trello-ops
```

**Published version:** 1.0.1

# Credentials

The module uses the RailCall vault provider `trello`.

Required credentials:

- Trello API key
- Trello user token

Credentials are retrieved through the RailCall vault and are not hard-coded in the module.

# Working Example

The `trello.create_card` command creates a Trello card.

**Example input:**

```json
{
  "idList": "<target-list-id>",
  "name": "RailCall Test Card",
  "desc": "Created through RailCall"
}
```

**Expected result:** A successful Trello API response containing the created card ID and card details, together with a valid RailCall execution receipt.

External write operations follow the **Preview → Approve → Execute → Signed Receipt** flow.

# Security

Network access is restricted to `api.trello.com`.

The handler uses Python standard-library HTTP functionality and requires no external Python packages. Subprocess execution is disabled, and credentials are retrieved through the RailCall vault.

Card responses are sanitized before being returned.

# Validation

The implemented commands were tested against real Trello resources and real API responses, including a successful cross-list card movement.

Expected API errors are surfaced rather than hidden.

# Known Limitations

Trello API credentials must be configured in the RailCall vault before execution.

Individual operations remain subject to Trello permissions and API behavior. The module does not bypass Trello permissions or silently retry failed operations.

# Module Information

**Module ID:** `manjeet-singh-2/trello-ops`

**Version:** `1.0.1`

**Category:** Ops

**Provider:** Trello
