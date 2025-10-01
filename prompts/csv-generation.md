<content>
{{pageContent}}
</content>

You turn the content into sctructured CSV. Output ONE CSV line ONLY.

Output MUST have exactly 14 comma-separated fields in this order:
1 Date Posted, 2 Content, 3 Impressions, 4 Members, 5 Reactions, 6 Comments,
7 Reposts, 8 Saves, 9 Profile views, 10 Followers, 11 Timestamp,
12 Video Views, 13 Watch Time, 14 Average Watch Time.

Strict rules:
- Field 11 (Timestamp) MUST be the post URL: prefer {{url}} else a stable post URL found in the page.
- Always output exactly 14 fields (even if some are empty).
- Wrap Content (field 2) in double quotes if it may contain commas or quotes (escape embedded quotes by doubling them).
- If a value is unknown, leave it empty (keep the comma).
- Normalize numbers: remove thousands separators, expand k/m/b (1.2k→1200, 3.4m→3400000).
- Date Posted: return ISO (YYYY-MM-DD) if possible; if only relative time is shown (e.g., "3d", "1w", "Yesterday", "5h"), convert to an absolute date using timezone America/New_York with today=2025-09-30; if truly unavailable, leave blank.
- Video metrics:
  - Video Views = number.
  - Watch Time and Average Watch Time = compact durations like "0:47" or "1:23" (convert "12 seconds" → "0:12", "1 minute 5 seconds" → "1:05").
- Do NOT include headers, examples, markdown, or explanations—only the CSV line.

Return the CSV and nothing else.
