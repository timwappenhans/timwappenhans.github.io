# timwappenhans.github.io

Tim's personal website. The `wc/` directory is the WM 2026 dashboard
(predictions, results, bracket, germany), rebuilt daily by the
`wc-dashboard-refresh` cloud routine and by local sessions.

## WC dashboard: data integrity rules (added 2026-07-02)

On June 28-July 1, 2026 the daily builds published fabricated results:
morning builds filled in overnight US games that sources had not yet
confirmed (invented scores, scorers, and narratives, including a Germany
"win" in a tie Germany lost on penalties), and later builds trusted the
site's own files, propagating the errors into wrong Round-of-32 pairings.
Corrected 2026-07-02. These rules are non-negotiable for every build:

1. **Every result, fixture, kickoff time, and standing comes from a
   fetched web source** (FIFA.com, ESPN, Wikipedia match pages). Anything
   NEW entering the site needs a second independent source.
2. **Never fill in a result the sources do not yet have.** A game that
   finished overnight US time may not be indexed by 08:00 Berlin. If it
   cannot be confirmed from a fetched page, write "pending", never a
   plausible score. A build with pending results is fine; a build with
   invented results is not.
3. **The site's own files are outputs, never inputs.** Re-derive knockout
   pairings and standings from a live source every build; never read them
   out of bracket.html or results.html.
4. **Research agents must return source URLs** and write NOT FOUND rather
   than estimate. Discard any claim that cannot be traced to a fetched
   page. Scorers and minutes only from a fetched match report.
5. **Verify the slate itself before building prediction cards**: confirm
   each fixture's two teams and kickoff time against the FIFA/ESPN
   schedule, not against yesterday's edition.

Card layout, language rules (American English, no em-dashes), and the
Kicktipp block spec live in `~/projects/wm2026/CLAUDE.md`; the committed
design is settled, do not re-litigate it. Prediction cards end with a
`.kt` block: shortest-priced correct scorelines (only if a book publishes
them, model/consensus labeled as such), over/under 2.5 + BTTS, tournament
xG per team, rest + travel, and a safe-vs-value Kicktipp pick row.
