<p align="center">
  <img src="assets/leadsagent.png" alt="LeadsAgent" width="96" height="96">
</p>

<h1 align="center">LeadsAgent for Claude</h1>

<p align="center">
  Find local businesses, research their contact details and get a ranked lead list, without leaving the chat.
</p>

<p align="center">
  <a href="https://leadsagent.io">Website</a> &nbsp;&middot;&nbsp;
  <a href="https://leadsagent.io/documentation/claude">Documentation</a> &nbsp;&middot;&nbsp;
  <a href="https://leadsagent.io/pricing">Pricing</a> &nbsp;&middot;&nbsp;
  <a href="https://leadsagent.io/contact-us">Support</a>
</p>

---

## What it does

Ask Claude for the businesses you want to reach. LeadsAgent searches 250M+ live business listings,
researches each one and returns a ranked list you can download as CSV.

> Find 50 dentists in Austin, TX with no website and get their emails.

For each lead you get:

| Data | Details |
|---|---|
| Business | Name, category, address, rating and review count |
| Contacts | Phone, website, emails found on the site, social profiles |
| Checks | Email verification, phone line type, website status, speed, security and technology |
| Fit | A score and the reasons the lead fits your offer |

Email finding, verification and all checks cost no credits. Each business researched costs one lead credit.

## Install

### Claude Code

```
/plugin marketplace add shanmaurya/leadsagent-plugin
/plugin install leadsagent@leadsagent
```

Then run `/mcp`, select **leadsagent** and sign in with your LeadsAgent account.

### Claude.ai and Claude Desktop

Open **Settings > Connectors > Add custom connector** and enter:

```
https://leadsagent.io/mcp/v1
```

Select **Connect** and sign in with your LeadsAgent account.

## How sign-in works

The connector uses OAuth 2.0. You sign in on leadsagent.io and approve access, and Claude receives a token
for your account. This repository holds no API keys, and you never paste a key into Claude.

Two scopes control what Claude can do:

| Scope | Allows |
|---|---|
| `leads:read` | Check credits, read tasks, lead lists and results |
| `leads:write` | Start searches and tasks, score leads, make lead lists and share links |

## Tools

| Tool | What it does | Type |
|---|---|---|
| `get_account` | Credits left, request limits and plan search limits | Read |
| `find_leads` | Runs a fixed search by category and location with the checks you turn on | Write |
| `start_task` | Gives a job in plain language to the LeadsAgent agent | Write |
| `reply_to_task` | Answers the agent's question or continues a finished task | Write |
| `get_task` | Status, progress, credits used and lead list counts | Read |
| `get_task_results` | A page of leads from a task, with filters | Read |
| `show_leads` | Shows the best leads as a table in the chat, with a CSV download | Read |
| `share_results` | Makes a public link to a lead list | Write |
| `search_tools` | Finds LeadsAgent tools for checks, scoring and lists | Read |
| `run_tool` | Runs one tool from `search_tools` on a task's lead list | Write |
| `start_extraction_run` | Starts search lanes for one location | Write |
| `global_timer` | Waits until a search lane ends or reaches its target | Read |
| `control_extraction_run` | Stops or replaces a search lane | Write |
| `count_session_leads` | Unique lead counts across lanes | Read |
| `list_artifacts` | Lists the lead lists of a task | Read |
| `read_leads` | Reads rows from a lead list | Read |
| `build_artifact_scoring_manifest` | Prepares leads for scoring | Read |
| `score_artifact_leads` | Scores leads against your offer | Write |
| `create_artifact` | Makes the final lead list | Write |

Every tool declares whether it is read-only, so Claude can ask before it runs a tool that starts work or spends credits.

## Example prompts

- Check my LeadsAgent account and credits.
- Find 100 plumbers in Denver with a phone number and a slow website.
- Score these leads for a website redesign offer and keep the top 25.
- Give me a CSV with only name, phone, email and website.

## Requirements

- A LeadsAgent account: [sign up](https://leadsagent.io/signup).
- Claude Code, Claude.ai or Claude Desktop on any plan that supports custom connectors.

## Privacy and data

LeadsAgent receives only the tool calls Claude sends: your search, the task and the arguments of each tool.
It does not read your conversations, files or Claude memory. Lead lists are saved in your LeadsAgent account.
Full details: [Privacy Policy](https://leadsagent.io/privacy) and
[Terms of Service](https://leadsagent.io/terms).

## Repository contents

```
.claude-plugin/plugin.json        Plugin manifest
.claude-plugin/marketplace.json   Lets Claude Code install the plugin from this repository
.mcp.json                         Connection to https://leadsagent.io/mcp/v1
assets/leadsagent.png             Icon
```

The LeadsAgent service runs on LeadsAgent's own servers. This repository contains no server code.

## Support

Email [support@leadsagent.io](mailto:support@leadsagent.io) or use the [contact form](https://leadsagent.io/contact-us).

## License

The files in this repository are released under the [MIT License](LICENSE). The LeadsAgent service, name and
logo are not covered by this license.
