*This repository is a mirror of the [component](http://component.io) module [bestander/jasmine](http://github.com/bestander/jasmine). It has been modified to work with NPM+Browserify. You can install it using the command `npm install npmcomponent/bestander-jasmine`. Please do not open issues or send pull requests against this repo. If you have issues with this repo, report it to [npmcomponent](https://github.com/airportyh/npmcomponent).*
<a name="README">[Jasmine](http://pivotal.github.com/jasmine/)</a> <a title="Build at Travis CI" href="http://travis-ci.org/#!/pivotal/jasmine"><img src="https://secure.travis-ci.org/pivotal/jasmine.png" /></a>
[![web component logo](https://component.jit.su/component-badge.svg)](https://github.com/component/component)
=======
**A JavaScript Testing Framework**

Jasmine is a Behavior Driven Development testing framework for JavaScript. It does not rely on browsers, DOM, or any JavaScript framework. Thus it's suited for websites, [Node.js](http://nodejs.org) projects, or anywhere that JavaScript can run.

Documentation & guides live here: [http://pivotal.github.com/jasmine/](http://pivotal.github.com/jasmine/)

## Component notes
The best way to use this component is to define it as a dev dependency in your component.json file.  
```json
  "development": {
    "bestander/jasmine": "*"
  }
```
Then in the spec-runner HTML do
```html
    <!-- no links to jasmine standalone component -->

    <!-- path to a `component(1)` built package -->
    <script type="text/javascript" src="../build/build-dev.js"></script>
    <script type="text/javascript" src="../build/build-dev.css"></script>

    <!-- list of your test spec files -->
    <script type="text/javascript" src="logic.spec.js"></script>
    <script type="text/javascript" src="moreLogic.spec.js"></script>
    <script type="text/javascript">
        (function () {
          var currentWindowOnload;
          var htmlReporter;
          var jasmine = require("<host name>/deps/jasmine").jasmine;
          var jasmineEnv = jasmine.getEnv();
          jasmineEnv.updateInterval = 1000;

          htmlReporter = new jasmine.HtmlReporter();

          jasmineEnv.addReporter(htmlReporter);

          jasmineEnv.specFilter = function (spec) {
            return htmlReporter.specFilter(spec);
          };

          currentWindowOnload = window.onload;

          window.onload = function () {
            if (currentWindowOnload) {
              currentWindowOnload();
            }
            execJasmine();
          };

          function execJasmine() {
            jasmineEnv.execute();
          }

        })();
    </script>
```

## Support

* Search past discussions: [http://groups.google.com/group/jasmine-js](http://groups.google.com/group/jasmine-js)
* Send an email to the list: [jasmine-js@googlegroups.com](jasmine-js@googlegroups.com)
* View the project backlog at Pivotal Tracker: [http://www.pivotaltracker.com/projects/10606](http://www.pivotaltracker.com/projects/10606)
* Follow us on Twitter: [@JasmineBDD](http://twitter.com/JasmineBDD)


## Maintainers

* [Davis W. Frank](mailto:dwfrank@pivotallabs.com), Pivotal Labs
* [Rajan Agaskar](mailto:rajan@pivotallabs.com), Pivotal Labs
* [Christian Williams](mailto:antixian666@gmail.com), Square

Copyright (c) 2008-2012 Pivotal Labs. This software is licensed under the MIT License.
