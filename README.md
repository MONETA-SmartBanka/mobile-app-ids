# mobile-app-ids

Shared source of truth for UI tests and analytics identifiers used across mobile platforms.

## Files

- `screen_ids.json` — screen-specific identifiers for test and analytics
- `component_ids.json` — reusable component identifiers

## Files structure

- each top-level group is an array of strings
- each string is only a logical key
- the final IDs are composed automatically by the generator

## Generated IDs

### Screens

For screens, the generator always creates the group ID itself:

```text
<prefix><group>
```

Example:

```text
SB: + smartbanka:settings
= SB:smartbanka:settings
```

If the group contains items, the generator also creates item IDs without the screen prefix:

```text
<group>:<item>
```

Example:

```text
smartbanka:settings + : + btn_logout_bottom
= smartbanka:settings:btn_logout_bottom
```

If the array is empty, only the group ID is generated.

### Components

For components, the generator behaves the same way, but usually without a prefix:

```text
<group>:<item>
```

Example:

```text
navigation_card
navigation_card:title
navigation_card:description
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
        "smartbanka:settings": [
            "btn_logout_bottom",
            "btn_card_limit",
            "btn_payments_limit",
            "btn_cvak_account",
            "btn_about_me"
        ]
    }
}
```

Generated IDs:

```text
SB:smartbanka:settings
smartbanka:settings:btn_logout_bottom
smartbanka:settings:btn_card_limit
smartbanka:settings:btn_payments_limit
smartbanka:settings:btn_cvak_account
smartbanka:settings:btn_about_me
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
            "title",
            "description",
            "value",
            "trailing_icon"
        ]
    }
}
```

Generated IDs:

```text
navigation_card
navigation_card:title
navigation_card:description
navigation_card:value
navigation_card:trailing_icon
```

## Conventions
- screen IDs should be same as existing analytics IDs
- use the `SB:` prefix for screens, no prefix for components
- a group with an empty array still generates its own group ID
- screen keys may use `:` for nested structure
- use `snake_case` for item names
- do not use visible text or localized strings as IDs
- keep IDs stable once they are used by automated tests
- duplicates are not allowed
- component groups should match real reusable UI components

## Platform-specific integration

Platform-specific generators and usage patterns should be documented in the iOS/Android repositories.
