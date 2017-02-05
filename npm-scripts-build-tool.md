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

- Pass arguments to npm scripts by adding `--` following the arguments

    ```javascript
    "scripts": {
        "watch:test": "npm test -- --watch"
    }
    ```    

- See **package variables** via `npm run env | grep "npm_package" | less`
    - `$npm_package_version` is handy

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
     


