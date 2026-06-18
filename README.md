# before-publish

📦 Best practices for npm packages before publish it to npm registry.

## List of best practices

- [ ] remove `dist/` directory from root directory

  - there is not need to keep compiled files in Git repository
  - this directory will be in package uploaded to npm registry

- [ ] add LICENSE file from root directory (if there is not one), you can use [MIT License](https://piecioshka.mit-license.org) template

  - https://github.com/search?q=owner%3Apiecioshka%20path%3ALICENSE&type=code

- [ ] run npm built-in command, to check if everything is ok (this command would fix some issues):

  ```bash
  npm pkg fix
  ```

- [ ] `.github/workflows/testing.yml`: support all Node.js version

  ```yml
  node-version: [10.x, 12.x, 14.x, 16.x, 18.x, 20.x, 22.x]
  ```

  Workflow file should has name `testing.yml`, so if there is a another workflow file with unit tests eg. `test.yml`, it should be renamed to `testing.yml`.

- [ ] `package.json`: remove `preferGlobal`

- [ ] `package.json/scripts`: replace all emoji nick to particular drawing

  - `:hammer:` -> 🔨
  - `:white_check_mark:` -> ✅
  - `:ledger:` -> 📒
  - `:clipboard:` -> 📋

- [ ] `package.json/scripts`: remove it's not necessary, because `git sync` will do it

  ```json
  {
    "postversion": "git push --tags"
  }
  ```

- [ ] `package.json/scripts`: add "version" to build changelog

  ```json
  {
    "version": "auto-changelog -p && git add CHANGELOG.md"
  }
  ```

- [ ] `package.json/devDependencies`: replace [istanbul](https://www.npmjs.com/package/istanbul) by [nyc](https://www.npmjs.com/package/nyc)

- [ ] `package.json/devDependencies`: replace [yargs](https://www.npmjs.com/package/yargs) by [minimist](https://www.npmjs.com/package/minimist)

- [ ] `package.json/devDependencies`: add `@types/jest` when `jest` is used

- [ ] `package.json/engines`: should includes:

  - `node`

- [ ] `.nvmrc` should be defined in the root directory (not direct version, but code name, e.g. `hydrogen` for Node.js 24)

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

- [ ] `package.json/files`: should not includes

  - `.github/`

- [ ] `package.json/files`: ignore spec files:

  ```json
  {
    "files": ["!**/*.spec.*"]
  }
  ```

- [ ] `package.json/main`: it should refers to `index.js` on the root level should be a main file

- [ ] `package.json/types`: it should refers to `types/index.d.ts`

- [ ] `package.json/repository`: it should be an object with `type` and `url` properties, not a string

  ```json
  "repository": {
    "type": "git",
    "url": "git+ssh://git@github.com/<username>>/<project_name>.git"
  },
  ```

- [ ] `package.json/author`: it should be an object with `name` and `email` properties, not a string

  ```json
  "author": {
    "name": "<name>",
    "email": "<email>",
    "url": "<url>"
  },
  ```

- [ ] `.gitignore`: should includes:

  ```text
  node_modules/
  npm-debug.log

  coverage/
  .nyc_output/
  dist/
  tmp/

  !.vscode/
  ```

- [ ] `README.md`: use this format for license section:

    ```md
    [The MIT License](https://piecioshka.mit-license.org) @ 2026
    ```

- [ ] `README.md`: update badges, should have:

  - cli available (optional)
  - node version
  - npm version
  - downloads count
  - size
  - license
  - github-ci (testing)

  Take a look at https://github.com/piecioshka/template-project

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
