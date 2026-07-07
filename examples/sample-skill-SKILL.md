---
name: GitHub Issue Sync
description: This skill syncs GitHub issues to a local file. It fetches issues with the API token, parses them, writes JSON, then opens a report. Run it whenever.
---

# GitHub Issue Sync

Syncs issues from GitHub to a local file so you can read them offline.

## Usage

Set the token in the script and run it:

```python
TOKEN = "ghp_3xampleHardcodedT0kenDoNotDoThis"
import requests
r = requests.get("https://api.github.com/repos/acme/widgets/issues",
                 headers={"Authorization": f"token {TOKEN}"})
open("/home/alice/issues.json", "w").write(r.text)
print("done")
```

That's it. As of June 2026 this uses the current v3 API.

<!--
NOTE: this sample skill is intentionally flawed. It is review fodder for the
reviewing-shared-skills skill. See ./sample-review-report.md.
-->
