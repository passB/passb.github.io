## Welcome to passb

### What is passb?

passb is a browser addon for the excellent [password store](https://passwordstore.org) command line password manager.

It is highly customizable to allow you to use it in the same style you use pass on the command line. 

### Installation

You can find passb in the [Firefox addon repository](https://addons.mozilla.org/firefox/addon/passb/) and soon in the Chrome addon store.

When you have installed the addon, you also have to install the host application and restart your browser.

This is documented here: [host application](./host_application.md)

### Customizing passb

passb allows you select certain *strategies* to reflect your pass usage.

#### Matcher Strategies

A matcher describes how you store your entries in the pass tree.
Currently, there are two matchers available:

* SimpleMatcher  
With the SimpleMatcher, passB looks for paths matching the url you currently are on. You can configure to ignore the prefix of the path (if you sort your domains into subfolders)and to ignore the last part of the path (if you use the filename as login name).
* FuzzaldrinMatcher  
The Fuzzaldrin matcher is a fuzzy matcher. It looks for the pass entries that seem to match the current url best.

#### FileFormat Strategies

A FileFormat Strategy describes how you store your data in your pass entry.

* FirstLineFileFormat  
This strategy assumes that you store your password in the first line of your pass entry. You can configure it to use the last part of your path as username, use the second line as username or assume that there is no username stored at all.
* PrefixFileFormat  
This strategy can be configured to look for prefixes like "password:", "login:" or "username:" in your pass entries. Also, as that use case is just too common, it can look for the password in the first line if you configure it to.

#### Filler Strategies

A filler strategy describes how a website should be filled.

* FillPasswordInputs  
This strategy just fills all password fields on the current page. Simple and effective.
* SelectorFiller
This strategy can be configured with css selectors to find password and username fields. Also, you can store page-specific css selectors in your pass entries.

### Extensions

These extensions can be enabled at will

* passB  
the passB core is an extension as well. There should not really be a reason to disable it, but if you want to: go for it.
* QR-Code  
this extension allows you to display a QR-Code of the current password for use with your mobile device.

## Extending passb

passB can easily be extended with new extensions or alternative strategies.

Take a look at the [QR-Code extension](https://github.com/passB/passB/tree/master/src/Extensions/QRCodeExtension) or the [FirstLine FileFormat](https://github.com/passB/passB/tree/master/src/PluggableStrategies/FileFormats/FirstLineFileFormat) as examples.

When creating an extension/strategy after one of these examples, please don't forget to register them with the [Dependency Injection Container](https://github.com/passB/passB/blob/master/src/Container.ts).

## Building & running it yourself

### Downloading passb & dependencies

```
git clone https://github.com/passB/passB.git
yarn
```

### Running it

(keep in mind that you should install the [host application](./host_application.html) too)

```
yarn run watch
yarn run remotedev #starts a local redux remote dev tools sever
yarn run start:firefox
```

### Running the tests

```
yarn run watch-tests
```

### Building it

```
yarn build
```

## Technology

technologies used are:

* [typescript](https://www.typescriptlang.org/) as language
* [react](https://reactjs.org) with [material-ui](https://material-ui-next.com/) for the user interface
* [redux](https://redux.js.org) with [immutable.js](https://facebook.github.io/immutable-js/) and [redux-persist](https://github.com/rt2zz/redux-persist) to keep options and data persistent between sessions
* [inversify-js](https://github.com/inversify/InversifyJS) for dependency injection
* [jest](https://facebook.github.io/jest/) with [enzyme](https://github.com/airbnb/enzyme) for tests 
* [yarn](https://yarnpkg.com) for package management and [webpack](https://github.com/webpack/webpack) for building 
