
### Build an NPM Package using Webpack and Babel

1. **Create Project Directory and Initialize npm:**

    ```bash
    mkdir test-package
    cd test-package/
    npm init -y
    ```

2. **Install React and React DOM as Development Dependencies:**

    ```bash
    npm install react react-dom --save-dev
    ```

3. **Add peerDependencies to package.json:**

    ```json
    "peerDependencies": {
        "react": "^18.2.0",
        "react-dom": "^18.2.0"
    }
    ```

4. **Create a src Directory and Add Component Files:**

    Create `src/index.js`:

    ```javascript
    export { default as Module } from "./module.js";
    ```

    Create `src/module.js`:

    ```javascript
    // Your module code here
    ```

5. **Install Webpack, Babel, and Necessary Loaders:**

    ```bash
    npm install @babel/core @babel/preset-env @babel/preset-react babel-loader webpack webpack-cli --save-dev
    ```

6. **Create .babelrc in Project Root:**

    ```json
    {
        "presets": ["@babel/preset-env", "@babel/preset-react"]
    }
    ```

7. **Create webpack.config.js in Project Root:**

    ```javascript
    const path = require("path");

    module.exports = {
        entry: "./src/index.js",
        output: {
            path: path.resolve(__dirname, "dist"),
            filename: "bundle.js",
            libraryTarget: "umd",
            library: "add-package",
            umdNamedDefine: true,
        },
        mode: "development",
        module: {
            rules: [
                {
                    test: /\.js$/,
                    exclude: /node_modules/,
                    use: {
                        loader: "babel-loader",
                    },
                },
                {
                    test: /\.css$/,
                    use: ["style-loader", "css-loader"],
                },
            ],
        },
    };
    ```

8. **Update package.json with Build Script:**

    ```json
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "build": "webpack"
    },
    ```

9. **Run the Build Script:**

    ```bash
    npm run build
    ```

10. **Login to npm Using Your Credentials:**

    ```bash
    npm login
    ```

11. **Publish Your Package:**

    ```bash
    npm publish
    ```

12. **Ensure Your Package Has a Unique Name.**

13. **To Update Your Package:**

    Run the Build Script Again:

    ```bash
    npm run build
    ```

    Bump the Package Version:

    ```bash
    npm version patch
    ```

    And Publish the Updated Package:

    ```bash
    npm publish
    ```

This process will ensure your package is updated and published with the latest changes.
