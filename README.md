## Vecteur Plus version
Build files based on version: https://github.com/vecteur-plus/ngTagsInput/tree/9f93df587d94df7fc21f7cb905fde868c49520af
Include pull-request 
	#141: https://github.com/mbenford/ngTagsInput/pull/141
	#142 https://github.com/mbenford/ngTagsInput/issues/142

# ngTagsInput [![Build Status](https://travis-ci.org/mbenford/ngTagsInput.png?branch=master)](https://travis-ci.org/mbenford/ngTagsInput) [![Coverage Status](https://coveralls.io/repos/mbenford/ngTagsInput/badge.png?branch=master)](https://coveralls.io/r/mbenford/ngTagsInput?branch=master) [![devDependency Status](https://david-dm.org/mbenford/ngTagsInput/dev-status.png)](https://david-dm.org/mbenford/ngTagsInput#info=devDependencies)

Tags input directive for AngularJS. Check out the [ngTagsInput website](http://mbenford.github.io/ngTagsInput) for more information.

## Requirements

 - AngularJS 1.2.1+ (v1.2.0 **is not** supported due to [an API change](https://github.com/angular/angular.js/commit/90f870) in Angular)
 - A modern browser

## Installing

The first step is to get the files. You have 3 options:

- Download the files manually from the [Releases page](https://github.com/mbenford/ngTagsInput/releases).
- Use Bower to download the files. Just run `bower install ng-tags-input`.
- Load the files from [CDNJS](http://cdnjs.com/libraries/ng-tags-input/).

Now all you have to do is add the scripts to your application. Just make sure the `ng-tags-input.js` file is inserted **after** the `angular.js` script:

```html
<script src="angular.js"></script>
<script src="ng-tags-input.js"></script>
<link rel="stylesheet" type="text/css" href="ng-tags-input.css">
```

## Usage

 1. Add the `ngTagsInput` module as a dependency in your AngularJS app;
 2. Add the custom directive `<tags-input>` to the HTML file where you want to use an input tag control and bind it to a property of your model. That property, if it exists, must be an array of objects and each object must have a property named `text` containing the tag text;
 3. Set up the options that make sense to your application;
 4. Enable autocomplete, if you want to use it, by adding the directive `<auto-complete>` inside the `<tags-input>` tag, and bind it to a function of your model. That function must return a promise that eventually resolves to an array of objects (same rule from step 2 applies here);
 5. Customize the CSS classes, if you want to.
 6. You're done!

**Note:** There's a more detailed [getting started](http://mbenford.github.io/ngTagsInput/gettingstarted) guide on the ngTagsInput website.

## Example

```html
<html>
<head>
    <script src="angular.min.js"></script>
    <script src="ng-tags-input.min.js"></script>
    <link rel="stylesheet" type="text/css" href="ng-tags-input.min.css">
    <script>
        angular.module('myApp', ['ngTagsInput'])
            .controller('MyCtrl', function($scope, $http) {
                $scope.tags = [
                    { text: 'just' },
                    { text: 'some' },
                    { text: 'cool' },
                    { text: 'tags' }
                ];
                $scope.loadTags = function(query) {
                     return $http.get('/tags?query=' + query);
                };
            });
    </script>
</head>
<body ng-app="myApp" ng-controller="MyCtrl">
    <tags-input ng-model="tags">
        <auto-complete source="loadTags($query)"></auto-complete>
    </tags-input>
</body>
</html>
```

## Options

Check out the [documentation](http://mbenford.github.io/ngTagsInput/documentation) page for a detailed view of all available options.

## Demo

You can see the directive in action in the [demo page](http://mbenford.github.io/ngTagsInput/demos).

## Contributing

See the [CONTRIBUTING](https://github.com/mbenford/ngTagsInput/blob/master/CONTRIBUTING.md) file.

## License

See the [LICENSE](https://github.com/mbenford/ngTagsInput/blob/master/LICENSE) file.

## Changelog

See the [CHANGELOG](https://github.com/mbenford/ngTagsInput/blob/master/CHANGELOG.md) page.

## Alternatives

The following are some alternatives to ngTagsInput you may want to check out:

- [angular-tags](http://decipherinc.github.io/angular-tags): Pure AngularJS tagging widget with typeahead support courtesy of ui-bootstrap
- [angular-tagger](https://github.com/monterail/angular-tagger): Pure Angular autocomplete with tags, no jQuery
- [jsTag](https://github.com/eranhirs/jstag): Open source project for editing tags (aka tokenizer) based on AngularJS
- [bootstrap-tagsinput](http://timschlechter.github.io/bootstrap-tagsinput/examples): jQuery plugin providing a Twitter Bootstrap user interface for managing tags (provides Angular support)
