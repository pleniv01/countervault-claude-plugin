# Countervault

Check a public receipt, compare a file fingerprint, and understand what the evidence establishes. Countervault helps preserve important digital records with dated receipts. This plugin adds a read-only verification workflow to your assistant.

## Try it

- Check this Countervault public receipt and explain its saved date.
- Compare this SHA-256 fingerprint with my public receipt. What does the match establish?
- Show me the synthetic Countervault demo and explain the limits of the evidence.
- How can I verify a private receipt using a proof bundle on my own device?

## Tools and access

`verify_public_receipt` fetches an existing public receipt and recomputes its sealed manifest. `compare_receipt_fingerprint` also checks a supplied SHA-256 against its entries. These tools do not retrieve original files or note text. They do not read private accounts, save or change records, enable sharing, create comparison events or submit blockchain timestamps. No account, payment or API key is required for the connector; Countervault's separate paid account features are not included.

Use only a receipt URL you intend to share for checking. Receipt links can grant access to public receipt metadata. Original files can stay on your device: calculate their SHA-256 locally and supply only the digest. The connector accepts Countervault receipt URLs, not arbitrary websites, private account links or credentials.

The skill uses the live public MCP URL declared in `.mcp.json`: https://countervault-mcp-production.up.railway.app/mcp. `claude --plugin-dir ./countervault-claude-plugin` loads the plugin. This package installs no dependencies and runs no local server or scripts. The separately hosted service source is at [countervault-mcp](https://github.com/pleniv01/countervault-mcp). Hosting the service does not itself publish a directory listing.

## What verification means

A matching digest supports byte integrity, not truth, authorship, ownership, identity, original creation date or legal admissibility. Countervault is not a legal notary. Claimed, source-attested and saved dates have different meanings. Reported anchor status is not independent cryptographic verification of a timestamp. Legacy v1 receipts have additional delimiter/metadata limits that the tools disclose.

The `demo` input is a synthetic fixture. Its receipt number explicitly says it is not a saved receipt; its dates and entries are fictional. It exercises real manifest and comparison code without accessing a customer's account. It is not a blockchain proof or a production account record.

## Privacy and support

Read [connector and plugin privacy](PRIVACY.md), [Countervault website privacy](https://api.countervault.co/privacy) and [terms](https://api.countervault.co/terms). For public integration support use [GitHub Issues](https://github.com/pleniv01/countervault-claude-plugin/issues). Do not post receipt links, credentials, fingerprints or private files in public issues. The website's private-contact instructions are on [Countervault's About page](https://api.countervault.co/about).

The plugin identifies Countervault at countervault.co. It is independent of Anthropic and OpenAI. The integration provides integrity checks and explanations; it does not provide legal advice. [MIT license](LICENSE) covers the plugin source and instructions; Countervault's brand and application are separate.
