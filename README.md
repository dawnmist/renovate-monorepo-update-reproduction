# Renovate issue with updating the remix monorepo packages

## Expected behaviour

The full set of `@remix-run` packages with source url of <https://github.com/remix-run/remix> should be being updated together.

## Actual behaviour

Only the `@remix-run` packages in the `devDependencies` for the project are being proposed to be updated.
The production dependencies get left out.

## Solution

The section that was causing the issue was:

```json
{
  "packageRules": [
    {
      "matchDepTypes": ["dependencies"],
      "allowedVersions": "<1.0.0",
      "separateMinorPatch": true,
      "minor": {
        "automerge": false
      }
    }
  ]
}
```

The `allowedVersion` was restricting dependency package updates to only those below version 1.0.0.
It should have used `matchCurrentVersion` instead, as it was intended to treat minor patches of versions less than 1.0.0 the same way that major patches for versions 1.0.0+ are treated.
