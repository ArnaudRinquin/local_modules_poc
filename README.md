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
* Install this local package in your top level module using: `npm install --save ./locale_modules/my-new-module`.
* ????
* Profit!

## Updating a local module

* Update whatever you want in your module (including dependencies)
* Bump your sub-module version (important)
* Simply run `npm update` or `npm update my-module`

## Pros

* No dirty hack, `require()` wrapper, `../../../` paths, but pure `npm`
* Proper nested 3rd party dependency declaration
* Super easy to externalize your local module and make it a 3rd party library if you feel like it: it already is an independent node module.

## Cons

* Requires (r|d)ecent `npm` version.
  * [ ] Nodejs™ `0.10.38` + `npm 1.4.28`, `install` fails
  * [ ] Nodejs™ `0.11.16` + `npm 2.3.0`, `update` fails
  * [X] Nodejs™ `0.12.2` + `npm 2.7.4`
  * [X] iojs `1.` + `npm 2.3.0`
* ???
