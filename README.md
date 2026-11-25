# Real Ability Scores Quiz

A self-contained, D&D-inspired real-world ability assessment. Open `index.html` in a browser or publish the repository with GitHub Pages.

## Features

- 30-question attempt drawn randomly from a 78-question bank (13 questions per ability).
- Five response options: Strongly disagree through Strongly agree.
- Five randomly selected questions per ability on each attempt, shuffled together.
- Weighted questions and reverse-scored statements.
- All six scores begin at 10; diminishing-returns scoring makes extreme results increasingly difficult.
- Results include a score, D&D-style ability modifier, qualitative interpretation, and a custom inline SVG emblem.
- Responsive layout, keyboard focus states, reduced-motion support, and print-friendly results.
- No build step, package manager, framework, backend, or external JavaScript dependency.

## Run locally

Double-click `index.html`, or serve the folder with any static web server. The quiz runs entirely in the browser and does not transmit or save answers.

## Publish with GitHub Pages

1. Open the repository's **Settings → Pages**.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select **main** and **/(root)**, then save.
4. GitHub will provide the published URL after deployment.

## Scoring model

Each ability starts at 10. Each selected question contributes a weighted response from -2 to +2; reverse-keyed questions invert that response. The weighted responses are normalized to a -1 to +1 range, transformed with a power curve, and mapped to an integer score from 1 to 20:

`score = round(10 + 10 × sign(r) × |r|^2.05)`

where `r` is the normalized weighted response for that ability. This deliberately compresses ordinary differences around 10 and makes scores near 1 or 20 rare. The D&D-style modifier is calculated as `floor((score - 10) / 2)`.

The question bank is randomized, so different attempts can produce different question sets. Because this is a short self-report quiz, results are approximate and should be treated as entertainment—not a validated psychometric, medical, IQ, or physical-performance assessment.

## D&D rules references

The six abilities and their core meanings follow the 2024 D&D Basic Rules / System Reference Document 5.2.1:

- [D&D Beyond — Playing the Game: The Six Abilities](https://www.dndbeyond.com/sources/dnd/br-2024/playing-the-game)
- [D&D Beyond — Creating a Character: Determine Ability Scores](https://www.dndbeyond.com/sources/dnd/br-2024/creating-a-character)
- [Wizards of the Coast — System Reference Document 5.2.1 (PDF)](https://media.dndbeyond.com/compendium-images/srd/5.2/SRD_CC_v5.2.1.pdf)

D&D describes 10–11 as the human average, 20 as the usual adventurer maximum, and 30 as the maximum possible score. This quiz adapts those concepts into an informal real-world scale; it does not claim that the quiz score is equivalent to an official D&D character-generation method or a scientific measurement.

## License and affiliation

This is an unofficial fan-made project and is not affiliated with, endorsed, sponsored, or specifically approved by Wizards of the Coast. Dungeons & Dragons is a trademark of Wizards of the Coast.
