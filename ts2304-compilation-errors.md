## How to fix TypeScript TS2304 compilation errors (and other ES6 compiling/transpiling issues)

```
TS2304: Cannot find name 'Map'.
TS2304: Cannot find name 'Set'.
TS2304: Cannot find name 'Promise'.
TS2304: Cannot find name 'MapConstructor'.
TS2304: Cannot find name 'SetConstructor'.
```

#### Method 1: Transpile into ES6

The easiest workaround is to simply switch the transpiler’s target from ES5 to ES6. To do that, change your `tsconfig.json` file to match the following values:

```json
{
  "compilerOptions": {
    "target": "es6",
    "module": "system",
    "moduleResolution": "node",
     ...
  },
  "exclude": [
    "node_modules",
    ...
  ]
}
```

However, doing that could bring in some issues: you could be unable to use some of your tools/packages/libraries who don’t support ES6 yet, such as [UglifyJS](https://github.com/mishoo/UglifyJS2/issues/448). If that’s not the case you’re good to go, otherwise keep reading.

### Method 2: Install Typings and core-js Type Definition Files

Before going for this method, ensure that your `tsconfig.json` file matches the following values:

```json
{
  "compilerOptions": {
    "target": "es5",
    "module": "system",
    "moduleResolution": "node",
     ...
  },
  "exclude": [
    "node_modules",
    ...
  ]
}
```

### Conclusions

While __Method 1__ is definitely trivial, what we did in __Method 2__ is also quite straightforward. We installed the __typings__ package through NPM, configured it to download some useful _type definition files_ (_core-js_ being the required one) using its very own `typings.json` config file, and finally we told our project to run it after each NPM task.

We might now be wondering about what [core-js](https://github.com/zloirock/core-js) actually is, so it could be wise to spend a couple words about it. Remember when we talked about shims a while ago? Well, core-js is our shim of choice, being it a general-purpose polyfill for ECMAScript 5 and ECMAScript 6 including the following: promises, symbols, collections, iterators, typed arrays, ECMAScript 7+ proposals, setImmediate, & much more. If you ever heard of [es6-shim](https://github.com/paulmillr/es6-shim), you can think about something that does that exact same job, but better.
