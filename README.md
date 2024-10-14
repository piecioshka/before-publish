# before-publish

📦 Best practices for npm packages before publish it to npm registry.

## List of best practices

- [ ] run npm built-in command, to check if everything is ok (this command would fix some issues):

  ```bash
  npm pkg fix
  ```

- [ ] `package.json`: replace [istanbul](https://www.npmjs.com/package/istanbul) by [nyc](https://www.npmjs.com/package/nyc)

- [ ] `package.json`: remove `preferGlobal`

- [ ] `package.json/engines`: should includes:

  - `node`

- [ ] `package.json/files`: should includes:

  - `demo/`
  - `dist/`
  - `docs/`
  - `src/`
  - `types/`
  - `index.js`
  - `package.json`
  - `LICENSE`
  - `README.md`

- [ ] `package.json/files`: do no add `.github/`

- [ ] `package.json/files`: ignore spec files:

  ```json
  {
    "files": ["!**/*.spec.*"]
  }
  ```

- [ ] `package.json/main`: it should refers to `index.js` on the root level should be a main file

- [ ] `package.json/types`: it should refers to `types/index.d.ts`

- [ ] `.gitignore`: should includes:

  - `node_modules/`
  - `npm-debug.log`
  - `coverage/`
  - `.nyc_output/`

- [ ] `README.md`: update URL for license badge to https://piecioshka.mit-license.org

- [ ] `README.md`: update badges, should have:

  - node version
  - npm version
  - downloads count
  - license
  - size
  - github-ci

- [ ] `.nycrc` for projects which use `nyc` and has spec files in the same directory as source files:

  ```json
  {
    "exclude": ["**/*.spec.*"]
  }
  ```

- [ ] `.markdownlint.json`: remove this file, left only for projects:
  - `*-guide`
  - `slides-*`
  - `*-workshop-*`
