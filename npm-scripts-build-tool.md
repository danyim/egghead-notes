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

So all in all, you should reference the local bins by just their name:

    ```javascript
    "scripts": {
        "eslint": "${npm bin}/eslint ..."
    }
    ```

### Handy "npm as a build tool" Packages
- `npm-run-all` Runs npm scripts optionally in parallel
    Usage: `npm-run-all --parallel lint:* build`


