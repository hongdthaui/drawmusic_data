# Draw Music sound data

SoundFont data for on-demand instrument downloads. This repository contains no application binaries or credentials.

- `soundfonts/core.sf2`: 17 core presets available for bundling in the app.
- `soundfonts/segmented/`: 274 individual SoundFonts, preserving original bank/program numbers.
- `soundfonts/segmented_manifest.json`: file names, byte lengths, SHA-256 checksums and instrument metadata.
- `soundfonts/instrument_catalog.json`: instrument display/catalog metadata.
- `release.json`: download configuration and core integrity information.

Segmented payload: 147,290,228 bytes. Individual files are at most 4,691,204 bytes.
The core bank is 2,001,788 bytes. Segment files include the 17 core presets for manifest completeness; clients can use the bundled core instead of downloading them.

## Integrity and caching

Download only a manifest-listed file, verify both its exact byte length and SHA-256, then atomically rename a temporary file into the private application cache. A failed or interrupted download must never be marked ready. Reuse verified files offline and offer retry on failure.

## Attribution and license

Sound bank: GeneralUser GS 2.0.3 BETA by S. Christian Collins. See [GeneralUser GS license](soundfonts/GeneralUser-GS-LICENSE.txt).
The full source bank has SHA-256 `9575028c7a1f589f5770fccc8cff2734566af40cd26ed836944e9a5152688cfe`.
Segmented files and manifest are preserved from the public `komtlabuketam/draw_music_banix` data repository, matched against the APK 2.7 manifest. See `soundfonts/provenance.json` for upstream provenance. The full source bank is not duplicated here.
