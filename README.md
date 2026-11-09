# StudioAnchor Reach

StudioAnchor Reach helps dance studios manage contacts, draft email campaigns, work with email sequences, and understand campaign results from Claude. This plugin provides five workflow skills around Reach's existing authenticated MCP connector.

## Workflows

- **Start:** identify the connected Reach workspace and available workflows.
- **Contacts:** find, add, edit, and organize contacts while preserving opt-outs and reviewing tag-triggered email effects.
- **Campaigns:** draft or revise emails, choose precise audiences, and prepare a specifically requested send for review.
- **Sequences:** draft and preview welcome series and follow-ups, then review separately requested activation, enrollment, or resume actions.
- **Reporting:** explain campaign, sequence, contact, signup, and reply results using read-only evidence.

Example requests:

- “Draft a registration email only for the contacts I select. Do not send it.”
- “Preview the second email in my welcome sequence.”
- “Explain how my recent campaigns performed and what is still waiting for approval.”

## Connect your workspace

You need a Reach account and access to the workspace you want to use. Install the plugin through Claude's directory when it is listed, then use Claude's normal OAuth connection flow. The server is `https://www.studioanchor.app/api/mcp`. Confirm the workspace name on the consent screen and in the initial workspace summary. Never put passwords, API keys, or tokens in a conversation.

Read-only work needs read access. Drafts and contact changes need write access. Sending email or starting automation needs send access and the workspace's applicable module entitlement. Real delivery also requires Reach's sender and compliance setup. If you already use the Reach connector, the plugin references the same endpoint so Claude can reuse one set of tools.

For local Claude Code evaluation before directory publication, point the supported plugin-directory option at an extracted plugin folder:

```sh
claude --plugin-dir /absolute/path/to/studioanchor-reach
```

## What the plugin does

The package contains readable workflow instructions and one remote MCP server declaration. It includes no local server, executable hook, installer, or bundled credentials. It connects only to StudioAnchor Reach; it does not call a second connector or invoke Reach's optional Ryla AI features.

Authorized tool calls may return workspace summaries, contact details, campaign content and analytics, sequence content and enrollment state, signup activity, or inbound replies. Requested writes are saved in Reach. The plugin adds no independent database. Reach's retention, deletion, service-provider, and security practices are described in its privacy policy; Claude's handling of conversation and tool results follows the user's Claude account settings and applicable terms.

## Review before email or destructive actions

Drafting and previewing do not send email. Campaign sends and sequence activation, enrollment, resume, and send-triggering tags use Reach's prepare/confirm protections. Review the exact prepared effect before confirming. Campaigns may additionally stop at `pending_approval` for an owner to approve inside Reach. That campaign setting is not a general hold on sequence delivery.

The skills preserve unsubscribed and bounced statuses, distinguish an email preview from a real test email, check unexpected audiences, and avoid silently replacing sequence sender settings. Contact notes and inbound replies are treated as data, not permission to take another action. Installing this plugin does not authorize a send, deletion, or broader OAuth access.

## Documentation, privacy, and support

- [Reach connection and tool guide](https://www.studioanchor.app/docs/reach-connectors)
- [Reach product](https://www.studioanchor.app/products/reach)
- [Support](https://www.studioanchor.app/support)
- [Privacy policy](https://www.studioanchor.app/privacy)
- [Terms of service](https://www.studioanchor.app/terms)
- [Security](https://www.studioanchor.app/security)

This is a StudioAnchor plugin maintained by Sivants, LLC. See the included LICENSE file for the workflow package's license; the Reach hosted service remains governed by its own terms.
