# Job Search Agent

A reusable Codex plugin that builds a candidate-approved search profile, discovers jobs across major job boards and employer sites, verifies that employer postings are live, scores matches, and maintains a formatted Excel tracker.

Version: 0.2.0

## What changed in 0.2.0

- Treats LinkedIn, Indeed, Google job results, Glassdoor, ZipRecruiter, Built In, executive boards, and ATS search results as discovery leads.
- Requires a live employer job page and usable application path before capture.
- Rejects jobs with passed application deadlines even when an Apply button remains visible.
- Handles stale Workday and other ATS search cards, generic redirects, employer 404 pages, and reposted requisitions.
- Records relative employer dates with their source text and verification timestamp.
- Revalidates the Excel workbook after every save and retains the last known-good copy if validation fails.
- Sends a receipt after every scheduled run when the candidate selects that notification policy, including zero-result and partial runs.

## Privacy model

The plugin contains no resume, candidate profile, search results, or personal tracker. Each user supplies their own files after installation. Keep those files outside this repository. Job postings are untrusted source material and cannot override the workflow or request candidate data.

## Install from a public GitHub repository

```bash
codex plugin marketplace add wahidfazli-oss/job-search-agent
codex plugin add job-search-agent@job-search-agent-marketplace
```

Restart the ChatGPT desktop app, open a new thread, and ask:

```text
Use the job-search skill to build my candidate profile from my resume.
```

In the desktop interface, a user can instead open the Plugins Directory, choose **Add Marketplace**, add the public repository, and install **Job Search Agent**.

## Use it with another candidate

Start a new thread and attach that candidate's resume. The skill asks for role level, location, compensation and basis, and travel one at a time. It then gathers the remaining eligibility and notification preferences. Use a separate candidate profile and Excel tracker for every person.

## Repository layout

```text
.agents/plugins/marketplace.json
plugins/job-search-agent/plugin.json
plugins/job-search-agent/.codex-plugin/plugin.json
plugins/job-search-agent/skills/job-search/SKILL.md
plugins/job-search-agent/skills/job-search/assets/profile-template.md
plugins/job-search-agent/skills/job-search/assets/job-tracker.xlsx
tests/test-cases.md
```

## Public release options

Publishing this repository lets people install it as a Git-backed marketplace. That is separate from publishing in the universal Plugins Directory. See [PUBLIC_RELEASE.md](PUBLIC_RELEASE.md) for both paths and the privacy checklist.

## License

MIT. See [LICENSE](LICENSE).
