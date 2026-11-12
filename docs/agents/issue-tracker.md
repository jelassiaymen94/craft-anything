# Issue tracker: Jira

Issues and specs for this repo live in the Jira project **DT** at
https://dreamyhomeguide-team-v4nzk0m0.atlassian.net/browse/DT. Use the Atlassian Jira tools
(read, search with JQL, create, update, comment). Never shell out to `gh` for issues.

`docs/ROADMAP.md` is the project plan and the source of truth for roadmap items (`R<milestone>.<n>`).
A Jira issue that implements a roadmap item names the id in its summary or description; it never
replaces the roadmap line, which still gets claimed and ticked as AGENTS.md says.

## Conventions

- **Create an issue**: `create_jira_issue` in DT. Type `Task` by default, `Bug` for defects, `Epic` for a spec or map.
- **Read an issue**: `get_jira_issue` with comments and links.
- **List issues**: `search_jira_using_jql`, e.g. `project = DT AND statusCategory != Done AND labels = ready-for-agent ORDER BY created`.
- **Parent / child**: create the child with `parent_issue` set to the Epic (or a `Subtask` under a Task).
- **Blocking**: a Jira "Blocks" issue link (child "is blocked by" blocker). An issue can be started when none of its blockers is unresolved.
- **Comment**: `update_jira_issue` with `comment_html`.
- **Labels**: `update_jira_issue` with `fields: {"labels": [...]}` (send the full list).
- **Close**: comment with the explanation, then transition to Done.

File issues only into DT. Never file into `mattpocock/skills`.

## Pull requests as a triage surface

**PRs as a request surface: no.** _(Set to `yes` if this repo treats external PRs as feature requests; `/triage` reads this flag.)_

## When a skill says "publish to the issue tracker"

Create a DT issue.

## When a skill says "fetch the relevant ticket"

Read it as in **Read an issue** above.

## Wayfinding operations

Used by `/wayfinder`.

- **Map**: an Epic labelled `wayfinder-map` holding Notes / Decisions so far / Fog.
- **Child ticket**: a Task with the map as parent, labelled `wayfinder-<type>` (`research`/`prototype`/`grilling`/`task`).
- **Frontier**: open children of the map with no unresolved blocker and no assignee; first by rank wins.
- **Claim**: assign it to yourself (the session's first write).
- **Resolve**: comment the answer, transition to Done, then add a pointer to it under the map's Decisions so far.
