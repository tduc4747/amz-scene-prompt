# Skill versions

Backups of `plugins/amz-image-prompts/skills/amz-scene-creator/SKILL.md`.

| File | Version | Notes |
|---|---|---|
| `v1.0-SKILL.md` | 1.0 (tag `v1.0`) | First build. Abstracts the REF away: strips stylised graphics such as a glowing shield, and builds a generic American room from the marker list instead of copying the REF's room. |
| — (live file) | 2.0 (tag `v2.0`) | REF drives the setting, the light and the graphic device. |

## Check which version ChatGPT actually loaded

Send the plugin the message `skill version` on its own. It replies with one line, e.g. `amz-scene-creator v2.0`.
If it answers anything else, ChatGPT is still running an old cached copy — remove and re-add the plugin.

## Roll back to 1.0

    copy versions\v1.0-SKILL.md plugins\amz-image-prompts\skills\amz-scene-creator\SKILL.md
    git commit -am "Roll back skill to v1.0"
    git push

Then remove and re-add the plugin in ChatGPT so it picks the change up.
