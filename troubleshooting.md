# Troubleshooting

## Connecting a CMS

**WordPress**
1. Install and enable the WordPress REST API on your site (on by default in modern
   WordPress) or an MCP-compatible plugin if your host requires one.
2. Generate an application password: WordPress admin -> Users -> Profile -> Application
   Passwords.
3. Add the WordPress MCP connector in your Claude client's connector settings, using your
   site URL and the application password.
4. Come back and run `/setup` again, or tell Claude directly, so it can set
   `your-setup/cms-connection.md` to `status: connected`.

**Webflow**
1. Generate a Webflow API token from Site Settings -> Apps & Integrations.
2. Add the Webflow MCP connector in your Claude client's connector settings.
3. Run `/setup` again to confirm the connection.

**Other CMS**
If your platform has a public API or an existing MCP server, the same pattern applies:
connect it in your Claude client, then run `/setup` to confirm. If none exists,
`format-for-publish` still works, it just defaults to a clean copy-paste document instead
of a live draft push.

## Connecting free research tools

**Google Search Console MCP**
Free. Search for an open-source Search Console MCP server, connect it with your Google
account that has Search Console access to your domain, then set
`google-search-console-mcp: on` in `your-setup/data-sources.md` (or just tell Claude
you've connected it and ask it to update the file).

**DataForSEO MCP**
Cheap, pay-per-call, no seat fee. Sign up for a DataForSEO account, get an API key, connect
the DataForSEO MCP server with it, then set `dataforseo-mcp: on` in `data-sources.md`.

## The pipeline says setup isn't done, but I already filled everything in

Check every file in `your-setup/` for a leftover `{{REPLACE_ME}}` token or a
`<!-- SETUP_INCOMPLETE -->` line at the top. Both must be gone from a file before the
engine treats it as configured. Run `/setup` again and it will find and fix whatever is
still marked incomplete.

## A step produced a bad result

You do not need to rerun the whole pipeline. Every step's output is saved to
`content/{step-number}-{step-name}/{slug}.md` (or `content/updates/...` for the update
pipeline). Open the file before the bad step to see what it was working from, fix that
file if needed, then ask Claude to re-run just that one skill.
