# Instructions for the slide-building agent

## Your deliverable

Create an editable academic slide deck titled **JEPA: Predicting Representations—from Images to Genomes** for a lab journal club on 8 September 2026. The presenter works in AI applied to genetics and clinical diagnosis; the audience includes researchers using protein and genomic language models and phylogenetics. The approved talk is **30 minutes: 14 main slides with 28 minutes of scripted explanation and 2 minutes of delivery margin**, followed by discussion if the session permits.

Use English throughout. The deliverable requested of you is the deck; these files already supply the scientific content and presenter preparation. Do not restart the scope interview. Routine visual and layout choices are yours. Presenter name and affiliation are not supplied: omit them or leave clearly labeled editable fields rather than inventing an identity.

## Read in this order

1. `01_SLIDE_SCRIPT.md`: authoritative main-slide sequence, on-screen content, complete narration, timing, transitions, and sources.
2. `04_SOURCE_EVIDENCE.md`: evidence limits, versioned references, exact table values, figure provenance, and mandatory corrections.
3. `03_BACKUP_QA_REHEARSAL.md`: ten optional backup slides with speaking answers; append them after the main talk.
4. `02_TECHNICAL_GUIDE.md`: deeper explanations and worked examples to resolve technical questions while building.
5. `assets/` and `data/`: original editable SVG illustrations and transcribed chart inputs.

The Markdown and data are authoritative if a visual simplification is ambiguous. The original schematic SVGs are editable starting points, not a complete slide deck. Where possible, recreate them as native slide objects and preserve the same information flow.

## Content and speaker notes

Build exactly 14 main slides in the approved order. Place each complete **Spoken script** in its slide's speaker notes. Add the transition, timing target, source links, and relevant technical caveats to those notes. Stage directions are silent. Do not paste the full narration into the visible slide.

Append backup slides B1–B10 with their supplied speaking answers. Distinguish their numbering from the timed main sequence. Append a readable bibliography slide or slides after the backups, based on the source register; these are reference material, not extra timed content. Use the source register's version and venue distinctions, including the proceedings confirmation that I-JEPA is CVPR 2023.

Keep the main-slide positive and negative genomic examples together. The complete DNABERT-2 Table 1 AUROC extract is in `data/dna_dnabert2_results.csv`. Never derive an average from the three selected main-slide examples and present it as the full benchmark.

## Visual specification

Use a 16:9 layout, generous margins, a white or very light background, and a restrained academic style. Use dark text with one consistent color per model role: teal for the context encoder, purple for the teacher, amber for the predictor. Pair colors with labels and arrow styles so the diagram remains understandable without color vision.

Aim for titles of at least 30 pt, body text of at least 22 pt, and clearly readable citations. Use short phrases on screen and one principal visual per slide. Render equations as editable mathematical text where supported. Reveal complicated diagrams in a few stages or use aligned static panels; the exported PDF must still make sense without animation. Show data arrows and EMA parameter-update arrows differently. Do not use decorative AI brains, fabricated biological imagery, or invented vector-coordinate meanings.

Cite author/year and source ID on scientific slides, with direct links in notes. Cite the specific table for numeric charts. The included SVG charts already retain protocol labels; do not crop those away. Their selected point estimates have no invented error bars or significance stars. Other paper figures have different licenses; use original schematics and transcribed facts where possible, with attribution. No external source PDFs are bundled as licensed stock assets.

## Scientific distinctions that must survive design

- JEPA is not an alternative category to a Transformer backbone.
- The I-JEPA teacher encodes the complete image before selecting target features; the context encoder cannot attend to hidden target input patches.
- The teacher is updated by EMA, not by the prediction-loss gradient.
- The paper-level squared-loss teaching equation differs from the released Smooth L1 implementation. Preserve that note.
- EMA and stop-gradient are not presented as a universal non-collapse theorem.
- I-JEPA evaluates teacher features; do not universally discard the teacher in an inference diagram.
- JEPA-DNA retains the language objective, predicts a global sequence representation, and has backbone-specific predictor/pooling paths.
- The genomic component control does not isolate a universally beneficial latent loss. Preserve preprint status, task-specific regressions, and the checkpoint-selection/uncertainty caveats in notes or backup B6.
- ProtJEPA is an abstract-supported qualitative sidebar. No full-method figure or numerical claim is supplied.
- Robotics transfer follows action-conditioned training. Clinical forecasting and proposed phylogenetic uses are not validated intervention or evolutionary models.

## Final verification and handoff

Render the deck and inspect every slide for overflow, small labels, broken symbols, bad contrast, unreadable sources, and incorrect arrows. Compare every chart value with the CSV and evidence ledger. Check that all 14 main slides contain their complete narration, that backup notes are present, and that the main timing totals 28 minutes plus margin. Do not claim that a word count is a measured rehearsal.

Return the editable deck, a PDF export if supported, and a short note identifying any unresolved rendering or scientific issue. Keep the final deck self-contained for presentation without internet access. No model training, experiment, publication, or message to other people is authorized by this handoff prompt.
