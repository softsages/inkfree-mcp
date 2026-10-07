# Inkfree MCP tools

32 tools. Generated from the production tool registry; do not edit by hand.

Access levels:

- **Read**: no changes to your account.
- **Write**: creates or edits records in your account.
- **Write (destructive)**: deletes, voids or cancels something. Clients should confirm with you first.
- **Sends email**: delivers email to real recipients. Clients should confirm with you first.

| Access | Tools |
| --- | --- |
| Read | 17 |
| Write | 7 |
| Write (destructive) | 4 |
| Sends email | 4 |

## Envelopes (sign requests)

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_inkfree_sign_request_audit_trail` | Read | Get the audit trail for one envelope: every recorded event (sent, viewed, signed, declined, voided) with who and when. |
| `mcp_inkfree_sign_request_bulk_send` | Sends email | Send an existing draft envelope to a list of recipients as separate single-signer envelopes, one per recipient. |
| `mcp_inkfree_sign_request_download` | Read | Get pre-signed download URLs for the document(s) in an Inkfree envelope. |
| `mcp_inkfree_sign_request_get` | Read | Get full details of one Inkfree envelope by id, including per-signer name/email/status/order. |
| `mcp_inkfree_sign_request_resend` | Sends email | Resend the signature reminder email for a pending Inkfree envelope. |
| `mcp_inkfree_sign_request_send` | Sends email | Send an existing Inkfree DRAFT envelope for signature. |
| `mcp_inkfree_sign_request_send_from_template` | Sends email | Send a new Inkfree envelope built from an existing template. |
| `mcp_inkfree_sign_request_void` | Write (destructive) | Void (cancel) a pending Inkfree envelope, stopping the outstanding signature request. |
| `mcp_inkfree_sign_requests_list` | Read | List the caller's e-signature envelopes, optionally filtered by status. |

## Organizing envelopes

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_inkfree_sign_request_delete` | Write (destructive) | Permanently delete an Inkfree envelope or an empty envelope folder. |
| `mcp_inkfree_sign_request_move` | Write | Move an Inkfree envelope or folder into a different folder. |
| `mcp_inkfree_sign_request_rename` | Write | Rename an Inkfree envelope or folder. |
| `mcp_inkfree_sign_requests_folder_create` | Write | Create a new folder for organizing Inkfree envelopes. |
| `mcp_inkfree_sign_requests_folders_tree` | Read | Get the full nested folder hierarchy for Inkfree envelopes (sign requests) in a single call (folders only, no envelopes themselves). |

## Sharing

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_inkfree_sign_request_share` | Write | Grant another user VIEW-only access to one Inkfree envelope, without making them a signer. |
| `mcp_inkfree_sign_request_share_revoke` | Write (destructive) | Revoke a previously-granted VIEW share on an Inkfree envelope. |
| `mcp_inkfree_sign_request_shares_list` | Read | List the active share grants (who has VIEW access) on one Inkfree envelope, including each share's id (needed to revoke it) and expiry. |

## Templates

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_inkfree_report_templates` | Read | Get a per-template usage report for a date range: envelopes sent and completed per template. |
| `mcp_inkfree_template_delete` | Write (destructive) | Permanently delete an Inkfree template or an empty template folder. |
| `mcp_inkfree_template_move` | Write | Move an Inkfree template or folder into a different folder. |
| `mcp_inkfree_template_rename` | Write | Rename an Inkfree template or folder. |
| `mcp_inkfree_templates_folder_create` | Write | Create a new folder for organizing Inkfree templates. |
| `mcp_inkfree_templates_folders_tree` | Read | Get the full nested folder hierarchy for Inkfree templates in a single call (folders only, no templates themselves). |
| `mcp_inkfree_templates_list` | Read | List the caller's Inkfree templates and folders. |
| `mcp_inkfree_webforms_by_template` | Read | List the webforms linked to one specific Inkfree template, one per signer slot that has a webform attached. |

## Webforms

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_inkfree_webforms_list` | Read | List the account's Inkfree webforms (public form pages linked to templates). |

## Reports

| Tool | Access | What it does |
| --- | --- | --- |
| `mcp_inkfree_report_audit_metrics` | Read | Get daily counts of audit events over a date range. |
| `mcp_inkfree_report_recipients` | Read | Get a per-recipient activity report for a date range: total/signed/pending envelope counts per recipient email. |
| `mcp_inkfree_report_request_counts_by_date` | Read | Get envelope funnel counts (sent, opened, completed) for a date range. |
| `mcp_inkfree_report_request_status_count` | Read | Get envelope counts by status over a date range. |
| `mcp_inkfree_request_counts` | Read | Get dashboard-style envelope counts for the caller: Pending, Signed, action required (needs the caller's action), and waiting for others. |
| `mcp_inkfree_user_report` | Read | Get per-user Inkfree activity: envelopes sent, envelopes completed, templates created. |
