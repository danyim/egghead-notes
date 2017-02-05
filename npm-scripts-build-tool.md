# How to Use npm Scripts as Your Build Tool

[Course Link](https://egghead.io/courses/how-to-use-npm-scripts-as-your-build-tool)

- In the `scripts` section, you might be tempted to prepend paths to the local versions of your tools (such as eslint):

    ```javascript
    "scripts": {
        "eslint": "./node_modules/.bin/eslint ..."
    }
    ```

    or

    ```javascript
    "scripts": {
        "eslint": "${npm bin}/eslint ..."
    }
    ```

    But by running `npm run env | grep "^PATH"`, you'll see that NPM automatically adds the local bin folder.

    So all in all, you should **reference the local bins by just their name**:

    ```javascript
    "scripts": {
        "eslint": "eslint ..."
    }
    ```

- Prepending the text `pre` or `post` for your script names will run them before or after the script respectively
    
    ```javascript
    "scripts": {
        "prebuild": "...", // <-- This runs BEFORE build
        "build": "...",
        "postbuild": "...", // <-- This runs AFTER build
    }
    ```

- Pass arguments to npm scripts by adding a `--` before the arguments

    ```javascript
    "scripts": {
        "watch:test": "npm test -- --watch"
    }
    ```    

- See **package variables** via `npm run env | grep "npm_package" | less`
    - `$npm_package_version` is handy

- To enable npm script completions in your shell, do `npm completions >> ~/.bashrc` (or `/.zshrc`) once

### Handy "npm as a build tool" packages
- `npm-run-all` - Runs npm scripts optionally in parallel
    - Usage: `npm-run-all --parallel lint:* build`
- `onchange` - watches for file changes
    - Usage: `onchange '**/*.js' -- npm run lint`
- `husky` - integrates git hooks with npm scripts
    - Usage: Add an npm task
    ```javascript
     "prepush": "npm run lint"
    ```
- `ntl` - npm task list, lists all tasks available in package.json
    - Usage: `ntl`
- `p-s` - package script; helps with managing external scripts outside of package.json
    - Usage: after moving your scripts out to `package-scripts.js`, you can run nps` to see a list of tasks


