# Generator-angm [![Build Status](https://travis-ci.org/newaeonweb/generator-angm.svg?branch=master)](https://travis-ci.org/newaeonweb/generator-angm) [![NPM Downloads](http://img.shields.io/npm/dm/generator-angm.svg)](https://www.npmjs.org/package/generator-angm) [![npm version](https://badge.fury.io/js/generator-angm.svg)](http://badge.fury.io/js/generator-angm)

AngularJS Yeoman Generator to help you getting started with a new project based on AngularJS and Angular Material to build large scale applications

> [Modular AngularJS Applications](http://www.newaeonweb.com.br/generator-angm) with Generator-angm

# Disclaimer
The main reason for creating this project, and do not use any other, was the need to optimize the creation time of each application from scratch.
It was built using the best practices of development with AngularJS and uses the latest stable version (1.5.0.).
The project does not intend to migrate to the new version(2.0) in a short time, we have in mind that this version is very stable and meets most web projects, so when version 2.0 is reasonably stable we do the migration.

## Getting Started

#### Installing Yeoman
Open your terminal window and type:

```bash
npm install -g yo
```

#### Installing the ANGM Generator

To install generator-angm from npm, run:

```bash
npm install -g generator-angm
```
#### Starting an application

From the command line, initiate the generator:

```bash
yo angm
```

## Running
Open your terminal window and type:

```bash
grunt dev
```

After the command your application should start right in your default browser at `localhost:8000`.
The `Gruntfile.js` already have some tasks like: Concat, Uglify, Injector and others.

> NOTE: after using **yo angm** command, we recorded some useful informations on **.yo-rc.json** file created at the project root folder. So you can't execute the generator command to create the application more than one time per folder!

# SubGenerators
Generator-angm have a subgenerator to create your application modules and directives, let's what we need to do to create modules.


#### Modules
To create a module just type on your teminal window:

```
yo angm:angm-module
```

After that you must entry the module name and choose what files you want.

The subgenerator will produce the following directory structure:

```
	moduleName/
		moduleName.html
		moduleNameModule.js
		moduleNameCtrl.js
		moduleNameRoute.js
		moduleNameService.js
		moduleName-test.js
```

**Note: Subgenerators are to be run from the root directory of your application.**


#### Content of each created files:
##### View (Html Template)
File: `app/modules/moduleName/moduleName.html`.

Code:
```html
<div>
	Content from: "Page = moduleName"
</div>
```
---
##### Controller

File: `app/modules/moduleName/moduleNameCtrl.js`.

Code:
```javascript
'use strict';

/**
 * @ngdoc function
 * @name appName.controller:moduleNameCtrl
 * @description
 * # moduleNameCtrl
 * Controller of the appName
 */
angular.module('appName')
	.controller('ModuleNameCtrl', ModuleNameCtrl);

	ModuleNameCtrl.$inject = ['Array of Dependencies optional'];

	function ModuleNameCtrl ('Array of Dependencies is the same above') {

	}

```
---

##### Route

File: `app/modules/moduleName/moduleNameRoute.js`.

Code:
```javascript
'use strict';

/**
 * @ngdoc function
 * @name appName.route:moduleNameRoute
 * @description
 * # moduleNameRoute
 * Route of the appName
 */
angular.module('appName')
	.config(function ($stateProvider) {
		$stateProvider
			.state('moduleName', {
				url: '/moduleName',
				templateUrl: 'appName/modules/moduleName/moduleName.html',
				controller: 'moduleNameCtrl',
				controllerAs: 'vm'
			});
	});
```
---

##### Module

File: `app/modules/moduleName/moduleNameModule.js`.

Code:
```javascript
'use strict';

/**
 * @ngdoc function
 * @name appName.route:moduleNameModule
 * @description
 * # moduleNameModule
 * Route of the appName
 */

 (function() {
   'use strict';

   angular.module('moduleName', []);

 })();
```
---

#### Directives
To create a directive just type on your terminal window:

```
yo angm:angm-directive
```

After that you must entry the directive name and choose what dependencies you want, by default we using external templates and external controllers.

The subgenerator will produce the following directory structure:

```
shared/
		directives/
			directiveName/
				assets/ /* optional folder
				directiveName.html
				directiveNameCtrl.j
				directiveName-test.js
```



## Injector
By default, new scripts are added to the `index.html` file. Using Grunt-injector, but only on setup configuration, after that you must run `grunt injector` or `grunt dev` every time you add a new module, directive or script.


## Bower Components

The following packages are always installed by the angm-generator:

* "json3"
* "es5-shim"
* "bootstrap"
* "angular"
* "angular-resource"
* "angular-aria"
* "angular-mocks"
* "angular-bootstrap"
* "angular-ui-router"


The following modules are optional on first install:

* "angular-cookies"
* "angular-animate"
* "angular-touch"
* "angular-sanitize"

All of these can be updated with `bower update` as new versions of AngularJS are released. Always on first install the generator will use the last stable version of all libraries.


## Testing

We implemented only one kind of test at this moment: Unit tests. On next weeks e2e tests will be available too.

### Running Tests

The tests are written in [Jasmine][jasmine], which we run with the [Karma Test Runner][karma]. We provide a Karma configuration file pre-configured with some default options to run them.

* the configuration is found at `karma.conf.js`
* the unit tests are found on each module created named as `moduleName-test.js`.

The easiest way to run the unit tests is to use the supplied npm script on `package.json` file:

```
npm test
```

This script will start the Karma test runner to execute the unit tests.


## Contribute

To submitting an issue, please check if pass on travis.

To submitting a bugfix, write a test that exposes the bug and fails before applying your fix.

To submitting a new feature, add tests that cover the feature.


## License

MIT
