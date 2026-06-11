# mobile-app-ids

Shared source of truth for UI automation identifiers used across mobile platforms.

## Files

- `automation_screen_ids.json` — screen-specific identifiers
- `automation_component_ids.json` — reusable component identifiers

## Files structure

- each top-level group is an array of strings
- each string is only a logical key
- the final automation ID is composed automatically by the generator

The resulting ID follows this rule:

```text
<prefix><group>_<item>
```

Example:

```text
sb_ + settings + _ + btn_logout_bottom
= sb_settings_btn_logout_bottom
```

## Example: screen manifest

```json
{
    "version": 1,
    "meta": {
        "namespace": "sb",
        "naming": {
            "prefix": "sb_"
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
        "namespace": "sb",
        "naming": {
            "prefix": "sb_"
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

- use the `sb_` prefix
- use `snake_case`
- do not use visible text or localized strings as IDs
- keep IDs stable once they are used by automated tests
- duplicates are not allowed
- component groups should match real reusable UI components

## Platform-specific integration

Platform-specific generators and usage patterns should be documented in the iOS/Android repositories.
