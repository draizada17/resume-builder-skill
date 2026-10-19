# My Fork Notes

Reference for how this local copy of `resume-builder-skill` is set up.

## My branch

- Branch: `docx-only-default`
- On GitHub: https://github.com/draizada17/resume-builder-skill/tree/docx-only-default
- What it changes: the skill asks whether you want a PDF before making a resume file. If you say no or don't answer clearly, it delivers only the `.docx`.
- The author's original version stays untouched on `master`.

## Remotes and tracking

| Remote     | Points to                                          | Purpose                    |
|------------|----------------------------------------------------|----------------------------|
| `origin`   | https://github.com/draizada17/resume-builder-skill | My fork (where I push)     |
| `upstream` | https://github.com/dabydat/resume-builder-skill    | Original author's repo     |

`docx-only-default` tracks `origin/docx-only-default`, so plain `git push` and `git pull` on this branch use my fork without any extra options.

## Getting the author's updates

```
cd "/Users/divyaraizada/Documents/[Agentic AI Developer] Career/resume-builder-skill"
git checkout docx-only-default
git fetch upstream
git merge upstream/master
git push
```

If the merge reports conflicts in `skill/SKILL.md` or `skill/references/format-and-structure.md`, keep my PDF-optional wording and add the author's other changes around it.

## Updating the installed skill

Claude uses the installed copy at `~/.claude/skills/resume-builder/`, not this repo. After merging updates or editing anything in `skill/`, copy it over again:

```
cp -R skill/. ~/.claude/skills/resume-builder/
```

## Logging in to GitHub

When `git push` asks for a password, use a GitHub personal access token with the **repo** scope, not your account password. macOS keeps it in the Keychain after the first use.
