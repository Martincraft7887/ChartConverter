# FNF Chart Converter

Convert chart JSON files between Leather Engine, Psych Engine / Psych Online, the V-Slice format used by the base game, and Codename Engine.

## Use it

1. Open `index.html` in a modern browser (or publish this folder with GitHub Pages).
2. Drop a chart JSON file into the page.
3. Check the detected source format and choose the target format.
4. Review the detected key count, then choose **Convertir chart** and download the result.

All processing is client-side. The chart stays in your browser.

## Preserved chart data

- Note time, lane, sustain length, and note type.
- Side/strum ownership; Leather note character when present and Codename strumline character lists.
- Per-side key counts on Leather. Psych Online multikey's combined lane convention is decoded as `lane + side × keyCount`; the key count is written in the chart's `keyCount` field.
- Song name, BPM, speed, common character fields, stage, events, and unknown source fields where applicable.
- A `_chartConverter` extension on converted formats retains character and source note data for further conversion.

## Compatibility notes

The engines do not share one chart schema. Psych Engine builds that do not implement Psych Online multikey may ignore `keyCount`; vanilla V-Slice has fewer per-note character controls than Leather; Codename charts may have multiple strumlines and extra engine-specific event data. The converter carries metadata in `_chartConverter` where possible, but each destination game only uses fields that its own loader recognizes. Check the converted chart in the destination engine before release.

This is a static HTML/JavaScript tool and requires no server, npm install, or build step. No upstream source code is bundled. Add a `LICENSE` file before redistributing the project under a chosen license.
