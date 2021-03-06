# eslint-config-netliferesearch
This package provides ESLint configs used in Netlife Research projects. The configurations are based on eslint-config-airbnb only differs on the tab size, using four space soft tabs.

For more details on the rules and how to work with the standard and ESLint itself see [Airbnb's Javascript styleguide](https://github.com/airbnb/javascript) and
the [ESlint config docs](http://eslint.org/docs/user-guide/configuring#extending-configuration-files).

## Installations
First, add the Netlife eslint and its peer dependencies to your project by executing the following command in your terminal;

```sh
(
  export PKG=eslint-config-netliferesearch;
  npm info "$PKG" peerDependencies --json | command sed 's/[\{\},]//g ; s/: /@/g' | xargs npm install --save-dev "$PKG"
)
```

Which produces and runs a command like:

```sh
npm i --save-dev eslint-config-netliferesearch eslint@^3.2.2 eslint-plugin-import@^1.12.0 eslint-plugin-jsx-a11y@^2.0.1 eslint-plugin-react@^6.0.0
```

Then create an `.eslintrc` file in the root of your project:

```json
{
  "extends": "netliferesearch"
}
```

## Alternative configurations
The default configuration (`netliferesearch`) expects your project to use the new ES6/2015 features. Depending on your project you might want or need something else, and a few other configs is provided:

* `netliferesearch/legacy` - A config for ES5 style projects.
* `netliferesearch/react` - A config for React+ES6/2015 projects.

## Configuration extensions
Extensions is used to alter the behavior in a consistent way across project, and reducing the need for overriding the standard in the `.eslintrc` file.

The extensions are not standards by them selves, but must be used in combination with one of the standards. When doing so, the `extends` key in the `.eslintrc` file is provided an array instead of a string, like this:

```json
{
  "extends": ["netliferesearch", "netliferesearch/angular"]
}
```

### Available extensions
* `netliferesearch/angular` - Disable rules that goes against the angular way of modifying the $scope.
