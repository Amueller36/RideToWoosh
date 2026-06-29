# Contributing

Thanks for your interest! This is a personal hobby project (provided as-is), but
issues and PRs are welcome.

## Reporting bugs

Open a **Bug report** issue and fill in the form — board model, core/library
versions, end device + app, and the Serial Monitor log make problems far faster to
fix. Check the README's **Troubleshooting** table first.

## Building

See the README's [Build & flash](README.md#build--flash-arduino-ide) section. All
files go in one folder named `RideToWooshHID/`. Target: ESP32-S3 + Arduino core 3.x,
NimBLE-Arduino ≥ 2.1.0.

## Common contributions

### Add a UI language

1. In `i18n.h`, copy the `LANG_EN_JSON` block to a new `LANG_XX_JSON` and translate
   every value (keep the keys).
2. In `RideToWooshHID.ino`, add a route `GET /i18n/xx.json` that serves it.
3. In `webui.h`, add a `<button data-lang="xx">XX</button>` to both `.seg` controls.

Translate **all** keys; English is the fallback when a key is missing.

### Add a key token

The firmware only emits keys handled in `pressToken()` (letters, digits, arrows,
`SPACE`, `ENTER`, `ESC`, `TAB`). To add one (e.g. a function key): handle it in
`pressToken()` in `RideToWooshHID.ino`, mirror it in `normKey()` in `webui.h`, and add
it to the on-screen picker (`buildPicker()`).

## Conventions

- Match the surrounding code style; keep the firmware in plain Arduino C++.
- UI changes: add strings to **both** `en.json` and `de.json`.
- Keep it brand-neutral — no Zwift/MyWhoosh logos, fonts or assets.
- Don't add AI-vendor attribution to commits or docs.

## License

By contributing you agree your contributions are licensed under the project's
**GPL-3.0** (see [LICENSE](LICENSE)).
