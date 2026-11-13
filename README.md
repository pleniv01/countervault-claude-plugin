# Countervault

Keep important records from your assistant: connect your Countervault account, find saved folders, preserve a requested note and generate a dated receipt. You can also check a public receipt or compare a locally computed file fingerprint.

## Try it

- Check this Countervault public receipt and explain its saved date.
- Compare this SHA-256 fingerprint with my public receipt. What does the match establish?
- Show me the synthetic Countervault demo and explain the limits of the evidence.
- How can I verify a private receipt using a proof bundle on my own device?
- Find my folder for the kitchen renovation and read the latest notes.
- Create a private folder for this project and save my own words as a note.
- Generate a receipt for the entries in that folder.

## Tools and access

Connect your account through Countervault's OAuth consent page. Read access enables `get_account_status`, `list_folders`, `get_folder` and `get_record_history`. Optional write access enables `create_folder`, `save_note` and `create_receipt`; existing folder permissions and subscription checks apply. New folders are private. These tools do not delete records, enable sharing, invite others, change billing or submit blockchain timestamps.

Countervault subscriptions are purchased and managed on the separate website. Public receipt checks require no account; account writes require an active subscription or an explicit complimentary account grant. Use the actual account-status result for current entitlement and price information. The plugin does not collect payment or promise a free paid plan.

`verify_public_receipt` recomputes an existing public receipt's manifest. `compare_receipt_fingerprint` checks a supplied digest against sealed entries. Those public tools do not return original files or note text. Account tools can return saved note text only after consent and the existing access checks.

Use only a receipt URL you intend to share for checking. Receipt links can grant access to public receipt metadata. Original files can stay on your device: calculate their SHA-256 locally and supply only the digest. The connector accepts Countervault receipt URLs, not arbitrary websites, private account links or credentials.

The skills use the live MCP URL declared in `.mcp.json`: https://countervault-mcp-production.up.railway.app/mcp. Public checks work without sign-in; account tools request OAuth. `claude --plugin-dir ./countervault-claude-plugin` loads the plugin. This package installs no dependencies and runs no local server or scripts. The separately hosted service source is at [countervault-mcp](https://github.com/pleniv01/countervault-mcp). Hosting the service does not itself publish a directory listing.

## What verification means

A matching digest supports byte integrity, not truth, authorship, ownership, identity, original creation date or legal admissibility. Countervault is not a legal notary. Claimed, source-attested and saved dates have different meanings. Reported anchor status is not independent cryptographic verification of a timestamp. Legacy v1 receipts have additional delimiter/metadata limits that the tools disclose.

The `demo` input is a synthetic fixture. Its receipt number explicitly says it is not a saved receipt; its dates and entries are fictional. It exercises real manifest and comparison code without accessing a customer's account. It is not a blockchain proof or a production account record.

## Privacy and support

Read [connector and plugin privacy](PRIVACY.md), [Countervault website privacy](https://api.countervault.co/privacy) and [terms](https://api.countervault.co/terms). For public integration support use [GitHub Issues](https://github.com/pleniv01/countervault-claude-plugin/issues). Do not post receipt links, credentials, fingerprints or private files in public issues. The website's private-contact instructions are on [Countervault's About page](https://api.countervault.co/about).

The plugin identifies Countervault at countervault.co. It is independent of Anthropic and OpenAI. The integration provides integrity checks and explanations; it does not provide legal advice. [MIT license](LICENSE) covers the plugin source and instructions; Countervault's brand and application are separate.

## Provenance update (0.3.0 review)

The paired MCP update preserves record source labels and requires explicit text_origin on save_note. User-authored notes stay receipted records; assistant analysis cannot be saved as a user-authored note. Until interpretation saving is implemented, that request returns saved=false. Receipt integrity does not establish truth or authorship. This package is a host integration, not a background model runner. Roll out with the corresponding reviewed API/MCP changes; changing package source does not publish a directory release.

## Record versions (0.4.0 review)

Read current entries with get_folder and earlier versions with get_record_history. The user can request a note correction with an explicit target, new text and reason; existing author/owner, write-access and storage rules apply. Earlier text and receipts remain unchanged. No deployment or directory publication is implied by this source update.

## Attachment storage (0.5.0 review)

Preserve returned storage_mode and content_stored separately: linked means a fingerprint/location, stored means Countervault retains content, and content_stored indicates a downloadable byte copy. Missing values on older results are unknown. get_account_status reports the same storage allowance used by web saves. Local attachments are selected, reviewed and uploaded in Countervault's website; MCP adds no file-upload/download tool. Never save copies, excerpts or images from linked files. A saved copy does not prove historical custody or the truth of its contents. Direct packet preparation to the website, where users explicitly choose whether to include saved copies.

This source update requires the paired API/MCP review branches; it does not publish a directory package or deploy production.
