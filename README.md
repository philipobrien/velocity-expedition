# Why Test?

### Types of Testing

1. End-to-End Testing (aka Acceptance, Functional)
2. Integration Testing
3. Unit Testing
4. Usability Testing
5. Load/Stress Testing
6. Performance Testing


#### End-to-End Testing
Tests execute as a client from the boundaries of the service.

* Test your Web UI via Browser Automation (Selenium + WebDriver)
* Test REST API via standard HTTP calls
* Cucumber, Nightwatch



#### Integration Testing
Tests run in regular Meteor context

* Meteor, Mongo, Template, Session on client
* Meteor, Mongo, process.env on Server
* Mocha, Jasmine, Tinytest, Laika



#### Unit Testing
Tests run in isolated context

* super fast
* have to mock/stub anything code depends on to run
* Jasmine




### Test Frameworks

#### Cucumber
[xolvio:cucumber](https://atmospherejs.com/xolvio/cucumber)
Describe behaviour in plain text and write step definitions. 

```
tests/
└── cucumber
    ├── features
    │   ├── sample.feature
    │   └── step_definitions
    │       └── sample_steps.js
    ├── fixtures
    │   └── my_fixture.js
```

#### Jasmine
[sanjo:jasmine](https://atmospherejs.com/sanjo/jasmine)


### Acknowledgements
[**Testing Meteor Applications** *Adrian Lanning & Abigail Watson*](http://slides.com/alanning55/testing-meteor-applications#/)