# AgentScope Documentation

This repository contains the unified documentation site for [AgentScope](https://github.com/agentscope-ai/agentscope) and [ReMe](https://github.com/agentscope-ai/ReMe). The site is built with [Mintlify](https://mintlify.com) and deployed at [docs.agentscope.io](https://docs.agentscope.io).

## Documentation Sets

- **AgentScope**: a framework for building agent applications.
- **ReMe**: a local-first, file-native memory layer for AI agents.

AgentScope maintains a bilingual version history. ReMe is updated in place under
`reme/latest/`, with a single bilingual navigation entry named `latest` in
`docs.json`.

## Local Development

Use an active Node.js LTS release (Node 20 or 22).

Install the [Mintlify CLI](https://www.npmjs.com/package/mint):

```bash
npm i -g mint
```

From the repository root, validate the site or start a preview:

```bash
mint validate
mint dev
```

The preview is available at `http://localhost:3000` by default.

## Repository Structure

```text
.
├── agentscope/
│   └── <version>/{en,zh}/   # Versioned AgentScope documentation
├── reme/
│   └── latest/{en,zh}/      # Current ReMe documentation
├── images/                  # Shared static assets
├── scripts/                 # Documentation maintenance scripts
├── docs.json                # Mintlify navigation and redirects
└── CLAUDE.md                # Writing and review guidelines
```

## Version Management

AgentScope documentation is immutable within each published version directory. For a new
AgentScope release:

1. Copy the latest relevant version into a new project version directory.
2. Update every version-specific internal link in the copied pages.
3. Add the version under the matching project tab for both languages in `docs.json`.
4. Point the relevant `latest` or `stable` redirect at the new version.
5. Run `mint validate` before submitting the change.

AgentScope versions can be created with `scripts/create-version.sh`.

ReMe does not keep historical release directories. Update `reme/latest/{en,zh}/`
directly, keep canonical internal links under `/reme/latest/...`, and leave its
`docs.json` version label as `latest`. The `/reme/stable/...` alias and obsolete
numeric-version URLs redirect to the current pages for compatibility.

## Contributing

When adding or updating documentation:

1. Place `.mdx` files in the correct project and language directory.
2. Update `docs.json` when pages or versions change.
3. Start every page with YAML frontmatter containing `title` and `description`.
4. Follow [CLAUDE.md](CLAUDE.md) for writing and review conventions.
5. Run `mint validate` before submitting a pull request.

## Resources

- [AgentScope GitHub](https://github.com/agentscope-ai/agentscope)
- [ReMe GitHub](https://github.com/agentscope-ai/ReMe)
- [Mintlify Documentation](https://mintlify.com/docs)
