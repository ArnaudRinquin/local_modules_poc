# local_modules usage Proof of Concept

Just a proof of concept of using `locale_modules` to to solve the ["Better local require() paths"](https://gist.github.com/branneman/8048520) problem.

It also helps you write true re-usable sub-modules.

## Running the app

Just like any node app:

```
npm install
npm start
```

_Note: This apps does nothing useful, it'll just print a useless array._

## Writing new sub modules

* Create a new folder in `local_modules`
* Create a `package.json` file for it, along with the usual `README.md`
* Adds its dependencies in its own `package.json`
* Write the module (duh)
* Install this local package in your top level module using: `npm install ./locale_modules/my-new-module`.
* ????
* Profit!

## Pros

* No dirty hack, `require()` wrapper, `../../../` paths, but pure `npm`
* Proper nested 3rd party dependency declaration
* Super easy to externalize your local module and make it a 3rd party library if you feel like it: it already is an independent node module.

## Cons

* If you modify your sub-module dependencies, you'll have to run `npm install` directly from `node_modules/my-module`.
