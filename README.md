# local_modules usage Proof of Concept

Just a proof of concept of using `local_modules` to to solve the ["Better local require() paths"](https://gist.github.com/branneman/8048520) problem.

It also helps you write true re-usable sub-modules.

## Running the app

Just like any node app:

```
npm install
npm start
```

_Note: This apps does nothing useful, it'll just print a useless array._

## Writing new sub modules

* Create a new folder for your module, such as `local_modules/my-module` (can be anything else)
* Create a `package.json` file for it, along with the usual `README.md`
* Adds its dependencies in its own `package.json`
* Write the module (duh)
* Install this local package in your top level module using: `npm install --save ./local_modules/my-new-module`.
* ????
* Profit!

## Updating a local module

* Update whatever you want in your module (including dependencies)
* Bump your sub-module version in its `package.json` (important)
* Simply run `npm update` or `npm update my-module`

## Pros

* No dirty hack, `require()` wrapper, `../../../` paths, but pure `npm`
* Proper nested 3rd party dependency declaration
* Super easy to externalize your local module and make it a 3rd party library if you feel like it: it already is an independent node module.

## Cons

* ~~The `npm update` of local module is [broken at the moment](https://github.com/npm/npm/issues/7426). Fingers crossed we can have it soon.~~ Fixed! And available since `npm 2.9.0` / `iojs 2.0.0`.
