# tmp-file-repro

Run `pnpm i` followed by `pnpm dry-run` (this script runs `wrangler deploy --config src/wrangler.jsonc --dry-run`).
Notice that a file named `.wrangler/tmp/deploy-[xxxxxx]/index.js` is included as an additional module.
This is mistakenly included when a config file in a subdirectory is used that contains the following configuration:

```json
"rules": [{ "type": "ESModule", "globs": ["**/*.js"] }],
"no_bundle": true
```
