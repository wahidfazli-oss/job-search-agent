# Public release instructions

## Option 1: Share through a public GitHub repository

1. Create an empty public GitHub repository.
2. Upload this repository's contents without changing the folder layout.
3. Confirm that `.agents/plugins/marketplace.json` points to `./plugins/job-search-agent`.
4. Inspect the repository before publishing. It must not contain a resume, candidate profile, completed tracker, search output, notification history, browser data, credentials, or local absolute paths.
5. Publish a tagged release such as `v0.2.0` and attach `job-search-agent-plugin-v0.2.0.zip` if desired.
6. Give users these commands:

   ```bash
   codex plugin marketplace add wahidfazli-oss/job-search-agent
   codex plugin add job-search-agent@job-search-agent-marketplace
   ```

7. Ask users to restart the ChatGPT desktop app and test the plugin in a new thread.

This method makes the source public and installable from the repository. It does not list the plugin in the universal Plugins Directory.

## Option 2: Publish in the universal Plugins Directory

1. Use an OpenAI Platform organization in which the submitter has **Apps Management: Write** permission.
2. Complete individual or business identity verification for the publisher.
3. Replace the generic `author.name` and `interface.developerName` values in the manifests with the verified publisher identity. Prepare a production name, short and long descriptions, logo, category, public website, support URL, privacy policy URL, and terms URL that match that identity.
4. Review the skill bundle, starter prompts, and the five positive and three negative cases in `tests/test-cases.md`.
5. In the plugin submission portal, create a **Skills only** submission and upload the final skill bundle.
6. Choose country availability, add release notes, complete the policy attestations, and submit for review.
7. After approval, publish from the portal. Only then will the plugin appear in the universal directory shared by ChatGPT and Codex.

Official guidance:

- [Package your plugin](https://developers.openai.com/plugins/build/plugins)
- [Submit plugins](https://developers.openai.com/plugins/deploy/submission)

## Privacy and security checklist

- The shared package contains only the blank profile and tracker templates.
- No resume, completed candidate profile, completed tracker, run receipt, or application history is included.
- No API keys, cookies, tokens, account IDs, or saved sessions are included.
- No local absolute paths or usernames appear in package text or workbook metadata.
- The skill does not apply, contact recruiters, upload resumes, or disclose candidate information without explicit approval.
- Search engines and aggregators are discovery sources. The employer's live page is required before a job is captured as verified.
- Candidate files remain separate by person and stay outside the plugin repository.
- Public website, support, privacy, and terms pages accurately describe any data handling before a universal-directory submission.

## Release checklist

1. Increment the semantic version in both plugin manifests.
2. Validate the skill and plugin.
3. Reopen the Excel template and confirm that Excel does not request a repair.
4. Run every test case in a clean thread with synthetic candidate data.
5. Scan the repository for personal data and absolute paths.
6. Build the archives from the clean repository tree.
7. Create a release tag and publish concise release notes.
