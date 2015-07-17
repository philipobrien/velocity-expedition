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


### BDD with Meteor & Cucumber
Describe your feature using [Gherkin syntax](https://github.com/cucumber/cucumber/wiki/Gherkin)

```
Feature: One-liner description of this feature

  As a [role]
  I want [feature]
  So that [benefit]

  The story above is to set context for the reader. It doesn't actually have any impact on the test
  itself. The phrases inside the scenarios are ties to test code using regex, which you can see in
  /tests/features/step_definitions/steps.js

  In this textual part of the file, you can include context about this feature, you can add links to
  external documents and whatever is needed to create the full specification.
  
  @dev
  Scenario: New user goes to home page
      Given I am a new user
      When I navigate to "/"
      Then I should see the title "velocity expedition"
```

Then when you save this file, you will get the following useful output in the log (that you better be tailing!)

```
@dev
  Scenario: New user goes to home page                # features/sample.feature:16
    Given I am a new user                             # features/sample.feature:17
    When I navigate to "/"                            # features/sample.feature:18
    Then I should see the title "velocity expedition" # features/sample.feature:19


1 scenario (1 undefined)
3 steps (3 undefined)

You can implement step definitions for undefined steps with these snippets:

this.Given(/^I am a new user$/, function (callback) {
  // Write code here that turns the phrase above into concrete actions
  callback.pending();
});

this.When(/^I navigate to "([^"]*)"$/, function (arg1, callback) {
  // Write code here that turns the phrase above into concrete actions
  callback.pending();
});

this.Then(/^I should see the title "([^"]*)"$/, function (arg1, callback) {
  // Write code here that turns the phrase above into concrete actions
  callback.pending();
});
```

It's up to you to then take these step-definition snippets, fill in the code to automate the scenario, and save the file.

You should then see a failing test

```
 @dev
  Scenario: New user goes to home page                # features/sample.feature:16
      Given I am a new user                             # features/sample.feature:17
      When I navigate to "/"                            # features/sample.feature:18
      Then I should see the title "velocity expedition" # features/sample.feature:19
        AssertionError: expected 'doomed expedition' to deeply equal 'velocity expedition'

1 scenario (1 failed)
3 steps (1 failed, 2 passed)
```

This lets you know the `title` is incorrect. Fixing it will get the test to pass.

```
@dev
  Scenario: New user goes to home page                # features/sample.feature:16
    Given I am a new user                             # features/sample.feature:17
    When I navigate to "/"                            # features/sample.feature:18
    Then I should see the title "velocity expedition" # features/sample.feature:19


1 scenario (1 passed)
3 steps (3 passed)
```


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
    └── fixtures
        └── my_fixture.js
```

Meteor Cucumber uses [WebdriverIO](http://webdriver.io/)

##### Fixtures
Any source file under `/tests/cucumber/fixtures` will be included on the mirror only, allowing you to have test-only code. 

##### Logging
Logs from the mirror and `cucumber` can be seen in the log file here:

```
velocity-expedition/.meteor/local/log/cucumber.log
```

You should `tail` this file to keep an eye on things `tail -f .meteor/local/log/cucumber.log`
#### Jasmine
[sanjo:jasmine](https://atmospherejs.com/sanjo/jasmine)


### Acknowledgements
[**Testing Meteor Applications** *Adrian Lanning & Abigail Watson*](http://slides.com/alanning55/testing-meteor-applications#/)