# OCR numeral fidelity

**Syamjith NK · Independent Researcher · Abu Dhabi, UAE**

**Public preprint v1.0.0 — not peer reviewed.**

When OCR Changes the Script, Does It Preserve the Number? A Controlled Evaluation of Numeral Recognition.

[Archived preprint and release](https://doi.org/10.5281/zenodo.23249467) · [Project and demonstration](https://syamjithnk.com/ocr-numeral-fidelity) · [Paper](OCR-Numeral-Fidelity-Preprint.pdf)

## What this study measures

Numeric value and numeral-script preservation are separate outcomes. We audit five OCR-capable open-weight models on 4,000 core and 3,000 robustness trials using archived outputs. The main non-Western core comparison contains 1,500 trials per prompt. Joint value-and-script success was 41/1,500 (2.73%) with the neutral prompt and 33/1,500 (2.20%) with preservation instructions. These are clean synthetic probes, not production failure rates or a ranking of all OCR systems.

The adjusted H1 observed-cluster contrast is -17.25 percentage points, but bootstrap calibration is inadequate. We do not assert calibrated H1 significance, an effect beyond 10 percentage points, or formal H2 equivalence. See the paper for both targets, both interval methods and all limitations.

## Download the complete source and data

[Download the versioned source and data ZIP](OCR-Numeral-Fidelity-v1.0.0.zip), extract it, and open the `ocr-numeral-fidelity` folder. All 97 package files and the SHA-256 manifest are inside. The layout below refers to that extracted folder.

## Reproduce the analysis

Use Python 3.12. Keep the environment and generated outputs outside this checkout.

```sh
python3 -m venv ../ocr-analysis-env
../ocr-analysis-env/bin/python -m pip install -r requirements-lock.txt
PYTHONDONTWRITEBYTECODE=1 ../ocr-analysis-env/bin/python code/test_release.py
PYTHONDONTWRITEBYTECODE=1 ../ocr-analysis-env/bin/python code/verify.py
PYTHONDONTWRITEBYTECODE=1 ../ocr-analysis-env/bin/python code/run_all.py --out ../ocr-reproduction --draws 2000 --workers 3
PYTHONDONTWRITEBYTECODE=1 ../ocr-analysis-env/bin/python code/verify.py --skip-manifest --results ../ocr-reproduction
```

Verification re-scores 7,000 trials and checks stored bootstrap arithmetic, paired tests and manifests. Full analysis reruns require 20,000 bootstrap refits. These commands make no model/API calls. Numeric differences across platforms are possible. Passing checks does not validate nominal interval coverage.

## Files and provenance

- `raw/`: unchanged archived model outputs.
- `protocol/`: original frozen records and post-analysis amendments. Hashes establish content integrity, not independent chronology.
- `code/`: scoring, analysis, calibration and checks.
- `results/`: corrected trials, summaries, draws and calibration diagnostics.
- `docs/Manuscript.pdf` and `.tex`: named public preprint.
- `docs/METHOD_DECISIONS.txt`: estimands, fitting and interval choices.
- `demo-examples.json`: three traceable, illustrative archived records, not a representative sample.

Historical correction notes record what was believed at each revision. Their old HOLD/status language is historical; this README and the public preprint describe this release. Public posting is not conference acceptance. The reviewer submission remains separate. Analysis/scoring code, observations and result files have not been changed for publicity. The manifest verifier now ignores Git metadata so that the same checks work in a Git checkout.

Original model revision hashes, font hashes and rendered stimuli are unavailable. The project demonstration reconstructs displayed numeral strings and labels that limitation; it is not a new model run. Exact original image-level reproduction is therefore qualified.

## Authorship and AI assistance

Syamjith NK led and directed the work. Author-operated AI agents, Claude and ChatGPT (called Astra by the author) assisted with code, analysis and writing; Codex assisted the documented correction and release workflow. Exact original model versions and per-tool task allocation are unavailable. AI systems are tools, not authors.

## Licences

Code: MIT (`LICENSE`). Non-software research materials: CC BY 4.0 (`LICENSE-DATA`). Third-party model/font rights remain with their holders; no weights or proprietary fonts are redistributed.

Please report reproducibility problems in repository issues with the file, command and expected/observed result. Independent replication and methodological criticism are welcome.
