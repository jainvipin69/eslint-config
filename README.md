# iNSight MicroFrontends Prettier Config
This project will be used as a centralised configuration for defining the best code standards to be followed on all 
microfrontend components.

# eslint-config
ESLint configuration for React Project. Easy to install and configure, it follows the best code standards from airbnb and uses prettier configuration on code format. Integrated with our [prettier configuration](https://github.com/prevoir/prettier-config) configuration

## Purpose
The purpose of creating this package is to extract, centralise, and standardise these rules, much like we currently do with SonarQube on the backend. To that end, we can create custom ESLint and Prettier packages with the necessary rules, and then import them directly into our micro frontends. This will allow the rules to be maintained independently from the actual code base.

## How to install
You need ESLint and Prettier installed as development dependencies on your project. You can install them by using **npm** or **yarn**.

#### NPM

```
npm install --save-dev eslint prettier
```

Install all peer dependencies of our configuration, these can be listed by the command:
```
npm info "@prevoir/eslint-config@latest" peerDependencies
```

If running *npm > v5* you install them by:
```
npx install-peerdeps --dev @prevoir/eslint-config
```

If *npm < v5*, Linux/OSX users can run:
```
(
  export PKG=@prevoir/eslint-config;
  npm info "$PKG@latest" peerDependencies --json | command sed 's/[\{\},]//g ; s/: /@/g' | xargs npm install --save-dev "$PKG@latest"
)
```

#### YARN

```
yarn add eslint prettier -D
```

Install the peer dependencies tool, by running:
```
yarn global add install-peerdeps
```

and after that run the following command to install the project's config:
```
install-peerdeps @prevoir/eslint-config
```

## How to use
To configure ESLinter and Prettier you can add to your `package.json`
```
"eslintConfig": {
  "extends": "@prevoir/eslint-config",
},
"prettier": "@prevoir/prettier-config"
```

Or create a `.eslintrc` and `.prettierrc` files and add `extends: "@prevoir/eslint-config"` and `"@prevoir/prettier-config"` respectivally. As an example:
```
<!-- .eslintrc -->
{
  "extends": "@prevoir/eslint-config"
  <!-- you can edit this configuration as usual, check ESLint docs -->
}

<!-- .prettierrc -->
"@prevoir/prettier-config"
```

To use ESLint and Prettier you can add this scripts to your `package.json` file
```
"lint": "eslint ./ --ignore-path .gitignore",
"lint:fix": "npm run lint -- --fix",
"format": "prettier --write \"{,!(node_modules)/**/}*.js\""
```