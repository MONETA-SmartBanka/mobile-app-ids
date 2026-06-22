# mobile-app-ids

Shared source of truth for UI automation and analytics identifiers used across mobile platforms.

## Files

- `screen_ids.json` — screen-specific identifiers for automation and analytics
- `component_ids.json` — reusable component identifiers

## Files structure

- each top-level group is an array of strings
- each string is only a logical key
- the final ID is composed automatically by the generator

The resulting ID follows this rule:

```text
<prefix><group>:<item>
```

Example:

```text
SB: + settings + : + btn_logout_bottom
= SB:settings:btn_logout_bottom
```

## Example: screen manifest

```json
{
    "version": 1,
    "meta": {
        "naming": {
            "prefix": "SB:"
        }
    },
    "screens": {
        "settings": [
            "root",
            "btn_logout_bottom",
            "btn_card_limit",
            "btn_payments_limit",
            "btn_cvak_account",
            "btn_about_me"
        ]
    }
}
```

## Example: component manifest

```json
{
    "version": 1,
    "meta": {
        "naming": {
            "prefix": ""
        }
    },
    "components": {
        "navigation_card": [
            "root",
            "title",
            "description",
            "value",
            "trailing_icon"
        ]
    }
}
```

## Conventions
- screen IDs should be same as existing analytics IDs
- use the `SB:` prefix for screens, no prefix for components
- use `snake_case` for item names
- do not use visible text or localized strings as IDs
- keep IDs stable once they are used by automated tests
- duplicates are not allowed
- component groups should match real reusable UI components

## Platform-specific integration

Platform-specific generators and usage patterns should be documented in the iOS/Android repositories.
