# Surge maintenance notes

- Project identity: repository `https://github.com/perryyeh/surge`, containing Surge rule lists and modules.
- Rule-list metadata rule:
  - When changing rules in a `.conf` file that already contains `# Size:` and `# Last Updated:` metadata, update both fields in the same commit.
  - Recalculate `# Size:` from the resulting file. Count every non-empty, non-comment line; do not count blank lines or lines whose first non-whitespace character is `#`.
  - Set `# Last Updated:` to the current UTC hour in ISO 8601 format: `YYYY-MM-DDTHH:00:00Z`. Do not include minute or second precision beyond `:00:00Z`.
  - The declared size must equal the counted rule lines, and the resulting list must not contain duplicate rule lines.
  - Do not add `Size` or `Last Updated` metadata to rule lists that do not already use those fields unless explicitly requested.
- Before pushing a rule-list change, validate that its declared size equals its non-comment, non-empty rule count, check for duplicate rules, and run `git diff --check`.
- Commit and push validated changes to `perryyeh/surge`.
- This is a public repository: do not add private infrastructure details, live addresses, credentials, or personal operational notes.
