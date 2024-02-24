# Renovate issue with updating the remix monorepo packages

## Expected behaviour

The full set of `@remix-run` packages with source url of <https://github.com/remix-run/remix> should be being updated together.

## Actual behaviour

Only the `@remix-run` packages in the `devDependencies` for the project are being proposed to be updated.
The production dependencies get left out.
