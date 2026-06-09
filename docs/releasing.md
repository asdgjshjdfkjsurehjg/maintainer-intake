# Releasing

Release checklist:

    npm ci
    npm run verify
    npm run build
    npm run build:action
    npm run verify:bundle
    npm run verify:pack
    npm run verify:security

Before a GitHub release:

1. Confirm the working tree is clean.
2. Confirm the Action bundle rebuild has zero diff.
3. Confirm package tarball contents and packed-install smoke pass.
4. Confirm public documentation commands pass.
5. Confirm public history contains no private files, tokens, or local-only material.
6. Confirm public CI is green.

GitHub release:

    git tag -a v0.1.0 -m "v0.1.0"
    git tag -f v0 v0.1.0

npm publication is a separate gate. Do not publish unless npm auth, name ownership, and registry install verification have passed.
