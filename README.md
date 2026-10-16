# RepairMind AI fan diagnostic prototype

RepairMind AI is a browser-based demonstration for structured, safety-first symptom triage of household electric fans. It asks symptom-dependent follow-up questions, applies visible hand-authored rules, and returns ranked possibilities with the observations that support them. When evidence is sparse it says so; when a safety warning is reported it stops troubleshooting and escalates.

## Prototype status and limits

This is a **developed software prototype**. Its diagnostic logic is a small, transparent rule set, not a trained AI, validated diagnostic system, or professional diagnosis. Relative rankings are not calibrated probabilities. It does not read free text, inspect an appliance, measure electrical values, or provide repair steps. It has not been tested with users, in homes, in a repair workshop, or in field deployment. Its automated tests cover the eight included example scenarios only and do not establish real-world accuracy or safety effectiveness.

## Run it

1. Open `index.html` in a current desktop or mobile browser. No installation, account, or server is needed.
2. Choose the closest symptom and answer the follow-up and safety questions based on existing observations.
3. If a safety stop appears, follow its escalation guidance. Do not use the app to justify continued use of a suspect fan.

The prototype has no external runtime dependencies or network calls.

## Run the sample tests

With Node.js 18 or later installed, from this folder run:

```text
node tests/run-tests.cjs
```

The runner checks expected outcome, expected top hypothesis where applicable, evidence presence for ranked hypotheses, and no fault rankings during safety stops. It uses only Node's built-in modules. `data/sample-cases.json` is the test dataset. `test-results.txt` records the actual run completed for this delivery. Browser-level interaction and visual rendering were not verified in this run.

## Diagnostic flow

The user chooses a symptom. Follow-up observations depend on that symptom. The rule engine adds simple positive or negative points to a short list of possible causes; only candidates with explicit supporting observations can be shown. The app describes the score only as a relative ordering. No evidence reaching the rule threshold produces an insufficient-evidence result. Any affirmative answer to the electrical/fire warning checklist bypasses the ranking and produces a stop-and-escalate outcome.

The rule definitions are in `assets/diagnostic.js`; the questions and result presentation are in `assets/app.js`. This is intentionally small enough for reviewers to inspect.

## Safety design

Warnings cover smoke/fire, burning smell or unusual heat, sparks or electric shock, damaged cord/plug, water exposure, and repeated breaker/fuse trips. The prototype tells users not to touch or open the fan, not to repeat a fault to gather evidence, and to seek qualified help. It does not direct a user to test live wiring or internal components. For active fire it advises moving away and contacting emergency services; power should be cut at a breaker only if safe. Safety guidance is informed by the U.S. Consumer Product Safety Commission's [Guide to Home Wiring Hazards](https://www.cpsc.gov/s3fs-public/518.pdf), which recommends stopping use and obtaining qualified repair for damaged appliance cords. Users should also follow local guidance and the fan manufacturer's instructions.

## Files

- `index.html` — application page.
- `assets/styles.css` — responsive visual styling.
- `assets/app.js` — structured questions, adaptive follow-ups, and rendering.
- `assets/diagnostic.js` — transparent rule-based diagnostic logic.
- `data/sample-cases.json` — eight illustrative cases, including uncertainty and safety stops.
- `tests/run-tests.cjs` — dependency-free test runner.
- `test-results.txt` — results from the actual run in this delivery environment.
- `SFIC-summary.md` — draft aligned to the supplied Innovation Format.
- `USER-GUIDE.md` — end-user explanation of the workflow, outcomes, and safety stops.

## Next validation steps

Before any real deployment, review the safety wording with a qualified electrical safety professional; validate the rules against a representative set of fan models and repair cases; test the interface with intended users; assess accessibility and browser/device behavior; and revise or remove unsupported rules. None of those activities is claimed as completed here.
