# How to Use npm Scripts as Your Build Tool

[Course Link](https://egghead.io/courses/how-to-use-npm-scripts-as-your-build-tool)

- In the `scripts` section, you might be tempted to prepend paths to the _local_ versions of your tools (such as eslint):

    ```javascript
        "eslint": "./node_modules/.bin/eslint ..."
    ```

    or 

    ```javascript
        "eslint": "${npm bin}/eslint ..."
    ```

