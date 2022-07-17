# babel-test

## Installation

- While you can install Babel CLI globally on your machine, it's much better to install it locally project by project.

- There are two primary reasons for this.

 1. Different projects on the same machine can depend on different versions of Babel allowing you to update one at a time.

 2. It means you do not have an implicit dependency on the environment you are working in. Making your project far more portable and easier to setup.

- We can install Babel CLI locally by running:

```
npm install --save-dev @babel/core @babel/cli
```


- Note: If you do not have a package.json, create one before installing. This will ensure proper interaction with the npx command.

- After that finishes installing, your package.json file should include:

```
{
  "devDependencies": {
+   "@babel/cli": "^7.0.0",
+   "@babel/core": "^7.0.0"
  }
}
```


## Usage

- Instead of running Babel directly from the command line we're going to put our commands in npm scripts which will use our local version.

- Simply add a "scripts" field to your package.json and put the babel command inside there as build.

```
  {
    "name": "my-project",
    "version": "1.0.0",
+   "scripts": {
+     "build": "babel src -d lib"
+   },
    "devDependencies": {
      "@babel/cli": "^7.0.0"
    }
  }
```
- Now from our terminal we can run:

```
npm run build
```


- This will run Babel the same way as before and the output will be present in lib directory, only now we are using a local copy.

- Alternatively, you can reference the babel cli inside of node_modules.

```
./node_modules/.bin/babel src -d lib
```


- For full documentation on the Babel CLI see the usage docs.

## Create babel.config.json configuration file

- Great! You've configured Babel but you haven't made it actually do anything. Create a babel.config.json config in your project root and enable some presets.

- To start, you can use the env preset, which enables transforms for ES2015+

```
npm install @babel/preset-env --save-dev
```


- In order to enable the preset you have to define it in your babel.config.json file, like this:

```
{
  "presets": ["@babel/preset-env"]
}
```
