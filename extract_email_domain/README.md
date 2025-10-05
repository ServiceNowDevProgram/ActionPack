This flow action retrieves the domain from an email address — it receives an email and returns the domain.

Extract the domain part of an email address—fast and reliably.

## What it does
Given an email string, returns the **domain** in lowercase.  
Supports:
- Plain emails: `user@sub.example.com`
- Angle-bracket style: `Jane Doe <jane@acme.co.uk>`
- `mailto:` prefixes


## Inputs
- **email** *(email, required)* — Any email-like string.

## Outputs
- **domain** *(String)* — Lowercased domain (e.g., `sub.example.com`). Empty if invalid.

## Usage

### In Flow Designer
1. Add **Email → Domain** to your flow.
2. Map **email** → e.g., `Current.caller_id.email` (or any string).
3. Use **outputs.domain** for routing, matching, or normalization.
