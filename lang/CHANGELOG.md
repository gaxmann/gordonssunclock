# Language files changelog

Keys that have been added, changed, or removed are listed here, as well as changes to the structure and/or language files that were added or removed, or whose support status changed.

## [1.6] - 2025-12-16
- Added: solcal_lph, lighttime, moon, buttonsolcal (unused), txlegende0 
- Structure: variables for certain list/dict entries added, currently: {solcal_lph|2} or whole list {solcal_lph|**}

## [1.5] - 2025-11
- Added: _meta (version, updated), ordinalsh (new key rules with gender distinction)
- Changed: xxdays (new keys for plural rules)
- Structure: variables for quoted labels added, e.g. {txgpsauto} or without quotes {txgpsauto-}; also special entry {auto}. Linefeed wildcard changed from [-LF-] to [~LF] because of conflicts with "wdiff | colordiff"  
- Files: fully supported ru.json added

## [1.4] - 2025-10
- Added: txpartsupport, txnosupport
- Structure: variable {LANGSUPPORT} added that automatically inserts txpartsupport or txnosupport if applicable

## [1.0..1.3] - 2025
- Initial structure and early changes
