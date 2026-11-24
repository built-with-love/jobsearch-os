# JobSearch OS

A free Claude plugin that runs your job search with Claude and the Google apps you already use. Claude drafts, files, tracks and prepares. You find the roles, decide, apply, interview, edit and send.

Read the full article: [JobSearch OS: How I run my job search with AI (and what I still do myself)](https://kevinsegedi.com/articles/jobsearch-os.html)

## Install

**Claude desktop app (Cowork):** open Customize, then Plugins, select Add marketplace, enter `built-with-love/jobsearch-os`, then install JobSearch OS.

**Claude Code:**

```
/plugin marketplace add built-with-love/jobsearch-os
/plugin install jobsearch-os@jobsearch-os
```

Then connect Gmail, Google Calendar, Google Drive, Google Docs and Google Sheets, and run `/setup`.

See [the plugin README](plugins/jobsearch-os/README.md) for what each skill does.

## Updating

The current version is listed in `plugins/jobsearch-os/.claude-plugin/plugin.json`.

**Claude Code:** run `/plugin marketplace update jobsearch-os`, then update the plugin.

**Claude desktop app (Cowork):** open Customize, then Plugins, and click Update on the JobSearch OS marketplace.

### Not seeing the latest version?

The desktop app sometimes keeps showing the version you first installed and says you're already up to date, even after a new version is published here. This is a known issue with plugins added from a GitHub marketplace, not with this plugin. Try these in order:

1. **Remove and re-add the marketplace.** In Customize, then Plugins, remove `built-with-love/jobsearch-os`. Quit and reopen the desktop app. Add the marketplace again and install JobSearch OS.
2. **Uninstall the plugin, then reinstall it** from the marketplace.
3. **Upload the plugin file directly.** Download this repository (Code, then Download ZIP), unzip it, and zip the contents of the `plugins/jobsearch-os` folder (not the folder itself). Rename the zip to `jobsearch-os.plugin` and upload it in Customize, then Plugins. Check the version again after you restart the app, because some people report it falling back to the old one.

If none of these work, the plugin still runs on the older version. You can follow the setup steps in the [article](https://kevinsegedi.com/articles/jobsearch-os.html) instead, or use Claude Code, which picks up updates with the command above.

## License

[CC BY-NC 4.0](https://creativecommons.org/licenses/by-nc/4.0/). Share and adapt it with credit to Kevin Segedi, but not for commercial use. Please don't package and sell it. Job searching is hard enough.
