# Yale Home for Home Assistant, test build

[![Validate](https://github.com/Yale-Libs/ha-yale/actions/workflows/validate.yml/badge.svg?branch=main)](https://github.com/Yale-Libs/ha-yale/actions/workflows/validate.yml)
[![HACS Custom](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://hacs.xyz/docs/faq/custom_repositories)

A copy of Home Assistant's built-in `yale` integration, taken from core 2026.11.0, that installs through HACS and replaces the built-in one while it is installed. It exists so the changes the [yalexs-ble activity log work](https://github.com/Yale-Libs/yalexs-ble/issues/421) asks of Home Assistant can be shown and tried end to end before they go to core.

This is a test build. It keeps the core domain `yale`, so your existing Yale Home entries keep working, and the built-in integration comes back when you uninstall it.

## Installation

1. In HACS, open the menu, choose Custom repositories, and add `https://github.com/Yale-Libs/ha-yale` as an Integration.
2. Install Yale Home and restart Home Assistant.
3. Existing Yale Home entries pick up the copy on restart; new ones are added the usual way under Settings, Devices & services.

## What changes here

- Adds `brand` to the `YaleXSBLEDiscovery` it sends to Yale Access Bluetooth for each lock with an offline key, so the library decodes that lock's activity log in Yale's numbering.

## Updating from core

`script/vendor <path to a home-assistant checkout> <tag>` checks out the tag there, builds the English translations with core's script, copies the integration in and sets the manifest's `version` to the tag. Commit the result before making changes on top, so the diff against core stays readable.

## License

The vendored code is Home Assistant's, under the Apache License 2.0 (see LICENSE).
