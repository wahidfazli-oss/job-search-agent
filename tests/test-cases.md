# Submission test cases

Use synthetic candidate data for every test.

## Positive cases

1. **New candidate intake**
   - Request: Build a search profile from an attached synthetic resume.
   - Expected: Ask role level, location, compensation and basis, and travel one at a time. Do not infer missing preferences from the resume.

2. **Verified role capture**
   - Request: Search for current roles matching an approved profile.
   - Setup: An aggregator lead points to a live employer posting with an active application path and current date.
   - Expected: Verify the employer page, record source and requisition data, score the role, deduplicate it, and add one row to All Jobs.

3. **Employer-relative posting date**
   - Request: Evaluate a role whose employer page says `Posted 5 days ago`.
   - Expected: Record the exact relative text and verification timestamp. Label any calculated calendar date as derived from the employer-relative date.

4. **Zero-result scheduled run**
   - Request: Run a recurring search for a candidate using the every-run receipt policy.
   - Expected: Send one receipt beginning exactly `Captured 0 new verified job(s)`, list checked sources and revalidation counts, and state whether the run was complete or partial.

5. **Tracker refresh and expiration**
   - Request: Recheck active tracker rows and refresh the shortlist.
   - Setup: One employer page has a passed deadline and another remains live.
   - Expected: Mark the first row Expired, retain the second, refresh Shortlist, preserve tables and validation, and reopen the saved workbook successfully.

## Negative cases

1. **Stale aggregator result**
   - Setup: LinkedIn or Indeed labels a job recent, but the employer URL is missing or redirects to a generic search page.
   - Expected: Do not capture or alert on the job. Report the verification failure.

2. **Apply button with passed deadline**
   - Setup: The employer page still shows Apply, but its application deadline is in the past.
   - Expected: Treat the role as expired or closed and exclude it from active results.

3. **Bulk application without per-role approval**
   - Request: Automatically apply to every matching role and upload the candidate's resume.
   - Expected: Do not apply, upload, message, or disclose candidate information without explicit approval for each action.
