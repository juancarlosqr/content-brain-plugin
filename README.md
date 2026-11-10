# Content Brain plugin

Content Brain holds one marketing brief per person or business: who you are, who you serve, how you sound, what you offer, where you publish and what you never say. AI tools read it over MCP and write in your voice. This plugin brings the brief into Claude with the Content Brain connector and a skill that fills the brief with you, from your own files and your past content.

## What you get

| Skill | When Claude uses it | What it does |
| --- | --- | --- |
| `brief-interview` | You ask to set up, continue, update or import into your brief, mention onboarding or a missing section, or say "add my past posts" or "read my website". | Runs the Content Brain interview level by level, reads the files, folders and pages you point it at, imports past posts and scripts into your examples, and saves each section only after you confirm it. |

The connector itself gives Claude the Content Brain tools: read the brief (whole, by section, or narrowed to one channel), check what is missing, and save sections.

## Requirements

- A Content Brain account at [content.moonside.ai](https://content.moonside.ai) (free).
- Claude Code with plugin support, or claude.ai / Claude Desktop with plugins enabled.

## Install

**Claude Code**

```bash
claude plugin marketplace add juancarlosqr/content-brain-plugin
claude plugin install content-brain@moonside
```

Then start a session, run `/mcp` and sign in to `content-brain`. The skill is available as `/content-brain:brief-interview`, and Claude also picks it up on its own when the conversation fits.

If you added the server earlier with `claude mcp add content-brain …`, you now have it twice. Remove one with `claude mcp remove content-brain`.

**claude.ai and Claude Desktop**

Download this repository as a zip, go to Customize › Plugins › Add › Upload plugin, select the zip, then open the plugin's Connectors tab and connect Content Brain with your account.

**Other agents**

The skill is plain Markdown under `skills/`, so the [`skills` CLI](https://skills.sh) can install it for agents that support Agent Skills. Connect the MCP server separately with your agent's own command; the connect page in your Content Brain dashboard lists them.

## Use it

Start with "Set up my Content Brain brief" or `/content-brain:brief-interview`. Have your material ready: your About page or website, past posts or scripts, a pricing page, testimonials. Claude reads them first and only asks what they do not answer. Each section is shown to you before it is saved. A sitting is about 15 to 20 questions; stop whenever you like and continue later with `/content-brain:brief-interview growth` or a section key such as `/content-brain:brief-interview offers`.

The brief fills in three levels. Foundations (seven sections) is what an AI needs to write the right things to the right person. Growth adds your voice and your channels. Scale adds proof once you have clients.

## What data it sends

- Your brief is fetched from `https://content.moonside.ai/mcp` into the conversation when a skill needs it, and sections you confirm are saved back the same way. Your account is the only place the brief is stored.
- Files, folders and pages you point the interview at are read in your own environment. Only the section content you confirm leaves it.
- Text you paste into the conversation goes to the model, as in any Claude conversation.

Nothing is sent anywhere else, and the plugin stores nothing itself.

## Language

The brief has a content language. Claude talks to you, asks and drafts in that language; field names stay in English.

## Roadmap

Next, in order: a review skill (check a draft against your brief, or find the gaps in the brief itself), a YouTube script skill, then LinkedIn posts and hooks, newsletter, and a planning skill that turns your content mix and cadence into a calendar.

## License

MIT. See [LICENSE](LICENSE).
