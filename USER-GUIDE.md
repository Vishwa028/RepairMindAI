# RepairMind AI user guide

## What this prototype does

RepairMind AI helps organize observations about an electric fan and shows a small, rule-based set of possible causes. It can also say that the answers are not specific enough to rank causes, or stop the flow when a safety warning is reported.

It does not inspect a fan, confirm a fault, give internal repair instructions, or replace a qualified repair professional. Its rankings are not probabilities.

## Start a symptom check

1. Open `index.html` in a recent browser.
2. Read the safety notice before entering symptoms.
3. Choose the fan type if known and select the closest main symptom.
4. Answer the follow-up questions from existing observations. “Not sure” is an acceptable answer. Do not recreate a fault to answer a question.
5. Complete the safety check. If you report a warning, the app stops and displays escalation guidance.
6. Review the outcome and the observations supporting each possibility. Share those observations with a qualified repair professional if you need help.

## Understand the outcomes

### Possible causes

The app displays up to three possibilities that pass its simple evidence threshold. Each possibility lists the observations that raised it, a short explanation, and a safe next step. The ordering comes from hand-authored point rules; it is not a likelihood estimate.

### Not enough evidence

The selected symptom and answers did not support a useful ranking. This is intentional. You can note when the problem happens and which external controls are affected, then ask a qualified repair professional. Do not use the app to justify continued operation if the fan seems unsafe.

### Safety stop

An affirmative answer about smoke/fire, burning smell or unusual heat, sparks or electric shock, damaged cord/plug, water exposure, or repeated breaker/fuse trips takes priority over fault estimates. Stop using the fan, do not touch or open it, and follow the on-screen escalation guidance. For active fire, move away and contact emergency services. Cut power at the breaker only if it is safe to do so.

## Things the app will never ask you to do

- Open the fan housing or remove a guard.
- Touch wiring, a capacitor, a motor, or any energized part.
- Test live electrical connections or deliberately reproduce a dangerous symptom.
- Keep using a fan after a safety stop.

## Try a few sample scenarios

The included dataset at `data/sample-cases.json` contains eight illustrative cases. They can be run with the test command in `README.md`. Example scenarios include humming without rotation, grinding noise, too little evidence, a damaged cord, and smoke. These are scripted software examples, not observed household cases or claims about how often faults occur.

## Feedback and limitations

The current prototype has not been evaluated with users, technicians, or a representative set of fan models. Feedback for a future validation round should focus on whether the questions are understandable, whether any wording encourages unsafe behavior, whether the evidence shown is traceable, and when the app should decline to rank. Any future deployment should involve qualified electrical-safety review and a clear route to professional assistance.
