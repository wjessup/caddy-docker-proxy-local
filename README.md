# Agent Skills

Reusable skills for AI coding agents (Cursor, Claude Code, Codex, and [37+ others](https://skills.sh/docs)).

## The Problem

When AI agents control your dev environment, you lose track of what's running where.

An agent starts `npm run dev` on port 3000 in one terminal. You open a second project — another agent grabs port 3000, fails silently, falls back to 3001. A third project takes 3002. Now you have three apps running on random ports across terminals you didn't open, and nobody — not you, not the agent — knows which URL belongs to which project.

This gets worse with multiple services. A fullstack app needs a frontend, API, and database. That's 3+ ports per project. Four projects running? You're juggling 12 port assignments that change every time something restarts.

**The fix:** move everything into Docker and put a reverse proxy in front. Each project gets a stable, human-readable URL like `http://my-project.localhost` regardless of how many projects are running. No port conflicts. No guessing. The agent doesn't need to track ports because there are none to track.

## Skills

### [caddy-docker-proxy-local](skills/caddy-docker-proxy-local/SKILL.md)

Sets up [caddy-docker-proxy](https://github.com/lucaslorentz/caddy-docker-proxy) for automatic `*.localhost` routing via Docker labels.

- One shared Caddy proxy runs on port 80 (machine-wide, set up once)
- Each project adds ~6 lines to `docker-compose.yml` to opt in
- Multiple projects run simultaneously with zero port conflicts
- URLs are deterministic: `http://<directory-name>.localhost`
- Works with any stack — the proxy doesn't care what's inside the container

```bash
npx skills add wjessup/agent-skills@caddy-docker-proxy-local
```

## Adding Skills

Each skill lives in `skills/<name>/SKILL.md`. PRs welcome.
