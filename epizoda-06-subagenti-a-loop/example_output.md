[refactor] d3 finally breaks up with CommonJS—the one dependency it could never `import` into its ESM life

**Summary:** The d3 umbrella package migrates from a CJS-first, three-target Rollup build to a pure-ESM module (`"type": "module"`), with a single `bundle.js` entry re-exporting `version` from `package.json` plus everything in `src/index.js`. Rollup now emits only UMD + minified UMD (the `d3.node.js` CJS target is gone). Tests swap `tape`/`tape-await` for `mocha`, `test-exports.js` is inlined into `d3-test.js`, and ESLint + a GitHub Actions workflow are added. The license flips BSD-3-Clause → ISC, all `d3-*` deps bump a major, and the floor is set at Node ≥ 12.

**BEHAVIOR**
- **Module system & entry point.** Replaces the CJS entry (`"main": "dist/d3.node.js"`, established in 5149a2f) with `"type": "module"`, `"main": "src/index.js"`, and an `exports` map; introduces `bundle.js` ... and renames `index.js` → `src/index.js`.
- **Rollup build.** Replaces the three-target config (cjs / umd / umd-min) wired with `rollup-plugin-node-resolve` and `json2module` (set up in 1126611) with a two-target config using `@rollup/plugin-node-resolve` + `@rollup/plugin-json` ...
- **Tests.** Replaces the `tape` harness and the `require()`-based `test-exports.js` helper (introduced in 6c71e02) with a single `mocha` file ...; deletes `test-exports.js` outright.
- **License.** Replaces the BSD-3-Clause text (year last bumped to 2020 in 5e516a5) with a shorter ISC clause, year 2010-2021.
- **CI & lint.** Introduces `.github/workflows/node.js.yml` (Node 14, `yarn --frozen-lockfile`, eslint, `yarn test`) ...
- **Docs & metadata.** Extends the README's v6 CDN `<script src>` snippets (added in 24f83a3) into ESM `import` blocks ...; Extends CHANGES.md (v6.0 notes last consolidated in 357c03e) by prepending a D3 7.0 section.
- **Sublime Text.** Reverses the `yarn test` build system and folder-exclusion setup added in ca06346 by deleting `d3.sublime-project` entirely.

**IMPACT**
*Confirmed*
- `API.md` references `index` → the rename `index.js` → `src/index.js` changes the resolution path for any consumer that deep-linked to the old top-level `index.js`; `package.json` now points `"module"` and `"main"` at `src/index.js` ...
*Possible*
- `yarn.lock` contains the substring `eslint` (treated as a plain-string hit...) → adding `eslint: 7` to `devDependencies` ... is a possible new hard-fail gate. (yarn.lock — uncertain: "no import/require/include/link line was found")
- ... (possible: yarn.lock `d3` majors bump; API.md `bundle` path)

**RECOMMENDED TESTS**
1. **Input:** `node -e "import('./src/index.js').then(m => console.log(m.version))"` ... **Coverage:** GAP (bundle.js is in COVERAGE GAPS).
2. **Input:** Run `yarn test` (mocha) in a clean `yarn --frozen-lockfile` install ... **Coverage:** existing test in `test/d3-test.js` (the new mocha loop).
3. **Input:** `rollup -c` then check `dist/d3.js` starts with the v6.7.0 banner and defines global `d3`. **Coverage:** GAP (rollup.config.js).
4. **Input:** `npx eslint src test --format=compact`. **Expected:** zero errors. **Coverage:** GAP (.eslintrc.json).
5. **Input:** `node` under Node 10. **Expected:** warn/refuse, `engines.node` is `>=12`. **Coverage:** GAP (package.json).

**EVIDENCE**
– 5149a2f  Mike Bostock  2021-04-15  6.7.0
– 6c71e02  Mike Bostock  2020-08-23  Update dependencies.
– 5e516a5  Mike Bostock  2020-09-02  Update year.
– 24f83a3  Philippe Rivière  2020-08-26  link to v6
– 357c03e  Mike Bostock  2020-08-27  Update CHANGES.
– 1126611  Mike Bostock  2019-11-20  Squelch Rollup warnings.
– ca06346  Mike Bostock  2018-08-24  Update dependencies.