<!-- SPDX-License-Identifier: Apache-2.0
     https://www.apache.org/licenses/LICENSE-2.0 -->

## Output format

Return ONLY valid JSON with this structure:

```json
{
  "resolved_base": "<SHA, or \"staged\">",
  "policy_ref": "<SHA>",
  "files_changed": 0,
  "lines_added": 0,
  "lines_removed": 0,
  "untracked_files": ["<path>"],
  "diff_empty": true | false,
  "stop_reason": "<message when diff_empty is true, else null>"
}
```

`resolved_base` is the commit the diff was taken against (the resolved explicit base or the merge base), or the literal `"staged"` for a staged-only review.
`policy_ref` is the commit Step 1 records for reading trusted project policy.
`files_changed`, `lines_added`, and `lines_removed` count the diff the skill reviews, not every command shown in the git state.
`untracked_files` lists the untracked files in the order git printed them; it is an empty list when there are none or for a staged-only review.
`diff_empty` is true when the reviewed diff is empty and the skill stops.
`stop_reason` is the human-facing message in that case; null otherwise.
Do not include any text outside the JSON object.
