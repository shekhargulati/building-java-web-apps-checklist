# ✅  building-java-web-apps-checklist ![](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)

This repository shares a checklist that I use for building web applications in Java+ Angular/React.

## :beginner: Before you start development

> ***Software architecture is the set of design decisions which, if made incorrectly, may cause your project to be cancelled. — Eoin Woods***

- [ ] Take architectural decisions. Finalize tech stack.
- [ ] Create a multi-module Maven or Gradle project for your development. Start with two modules — `backend` and `frontend`.  You can refer to [spring-boot-react-maven-starter](https://github.com/shekhargulati/spring-boot-react-maven-starter) for inspiration. `backend` contains Java code of the application. `frontend` contains all React/Angular JavaScript/TypeScript code of the application.
- [ ] You should use [Maven](https://github.com/takari/maven-wrapper) or [Gradle](https://docs.gradle.org/current/userguide/gradle_wrapper.html) wrapper scripts so that a new developer do not need to install Maven or Gradle on their machine before executing the build.
- [ ] Build project as a single jar/war using a single command i.e. if I am using Maven as my build tool then I should be able to run `./mvnw clean install` in the project root to build the executable.
- [ ] Set up CI server and make sure it can build the project as a single executable.
- [ ] Fix standup time and make sure it works for everyone.
- [ ] Finalise your sprint duration. 
- [ ] Finalise your testing strategy both manual and automated.
- [ ] Each team member should come up with their learning goal.

## :computer: During Development

### [Git](https://www.atlassian.com/git)

- [ ] Work on feature branches.
- [ ] Branch out from `develop` branch.
- [ ] Never push to `master` or `develop`. Make a pull request.
- [ ] Create PR on the `develop` branch and once it is tested then only merge to master. You can use different strategy like merge to `master` once sprint finishes.
- [ ] Delete local and remote branches after merging. You can automate this process as well.
- [ ] Before raising PR, run the build locally and make sure all tests pass.
- [ ] Use `.gitignore` file.
- [ ] Protect your `master` branch.
- [ ] Never commit binary files to Git.
- [ ] Write meaningful Git commit messages. [Read Chris Beam post on it](https://chris.beams.io/posts/git-commit/).
- [ ] Feature branches should be short lived.

### [Continuous Integration](https://martinfowler.com/articles/continuousIntegration.html)

> ***The most important practice for continuous integration to work properly is frequent check-ins to trunk or mainline. You should be checking in your code at least a couple of times a day. — David Farley***

- [ ] Every code committed to version control system mainline should trigger a continuous integration job that runs on the integration server.
- [ ] Continuous integration job should build the project and run all unit test cases. It should happen on each code commit to mainline.
- [ ] Fix broken builds immediately. CI server should always be in healthy green state.
- [ ] Make CI server visible and transparent to whole team.
- [ ] Maintain build jobs as code use `Jenkinsfile` if you are using Jenkins
- [ ] You should be able to create build jobs on a new CI server using code.
- [ ] Use pull request builder to build the project when pull request is raised.


### [Documentation](https://robots.thoughtbot.com/how-to-write-a-great-readme)

> ***Documentation is the castor oil of programming. Managers think it is good for programmers and programmers hate it!. — Gerald Weinberg***

- [ ] Create `README.md` file in root of your project and keep it updated. The README file should have following:
- [ ] Couple of lines describing purpose of the project.
- [ ] Instruction to grab the latest code and detailed instructions to build it.
- [ ] Instructions to run the project on local machine.
- [ ] Link to Continuous integration server.
- [ ] Instruction to do any setup required for the project.
- [ ] Instruction to grab project documentation.
- [ ] Any other relevant information that can help a new developer get started with the project.

### Code Style

> ***Style distinguishes excellence from accomplishment. — James Coplien***

- [ ] For backend, use [Checkstyle](http://checkstyle.sourceforge.net/) in your project. Make sure you it is integrated with the build.
- [ ] For frontend, use ESLint or [TSLint](https://palantir.github.io/tslint/).
- [ ] Format your code before committing.

### Testing

> ***Program testing can be used to show the presence of bugs, but never to show their absence! — Edsger Dijkstra***

- [ ] Write one automated functional test per user story.
- [ ] Cover business logic with unit/Integration tests.
- [ ] Understand different between unit testing and integration testing.
- [ ] Use consistent names for tests. I prefer to use `*Tests` as suffix for my tests.
- [ ] Use consistent naming strategy for tests like `shouldRegisterNewUser` or `registerNewUser` or `should_register_new_user`

### Dependencies

- [ ] Add a new dependency to the project after discussing with the team.
- [ ] Use [Snyk](https://snyk.io/) to check security vulnerabilities.
- [ ] Don't add dependency for each problem you face. First check if you already have some dependency that solves the problem.

### Learning

> ***You have to learn the rules of the game. And then you have to play better than anyone else. — Albert Einstein***

- [ ] Spend one hour on learning every day.
- [ ] Give session at your office or local meetup.
- [ ] Write blogs.

### Naming

> ***There are only two hard things in computer science: Cache Invalidation and Naming Things — Phil Karlton***

- [ ] Think and discuss with team before choosing a name for public member.
- [ ] Java and JavaScript use PascalCase for classes, interfaces, enums, annotations.
- [ ] Java and JavaScript use camelCase for methods and variables.

### Exception Handling

- [ ] Catch any checked exception thrown by the code.
- [ ] Convert checked exception to unchecked exception.
- [ ] Throw the unchecked exception. Unchecked exception could be custom or plain RuntimeException.
- [ ] Always use two arguments constructor of RuntimeException. The first take a message, second is the actual exception.
- [ ] Catch all exceptions thrown by code in your Controller or Resource classes.
- [ ] Log exceptions only in the Controller or Resource classes.
- [ ] Log both the message and exception. If using slf4j, then use `log.error(“message”,e)`.

### Logging
- [ ] Use slf4j with logback for logging.
- [ ] My applications logs all errors
- [ ] The log files are rotated

### REST API Design

- [ ] Pick a versioning strategy. If you don't understand pros and cons of different strategies then pick URL versioning scheme `/api/v1`. Twitter uses this versioning scheme.
- [ ] Resources are nouns.
- [ ] Use HTTP `POST` for creating a resource on the server or for taking action. Always return location of created entity in the `Location` header.
- [ ] Use `PATCH` HTTP method for update for partial update.
- [ ] Use `PUT` HTTP method when you do full update i.e. when client sends all the information in the request.
- [ ] Use `DELETE` HTTP method to delete a resource on the server
- [ ] For mapping actions use a consistent strategy. I recommend using `resource_name/actions/:action` strategy. For example, REST API for implementing `like` functionality you will make HTTP POST request to  `/api/v1/posts/123/actions/like` URL.
- [ ] In the above example if you have to implement undo action then you can make HTTP DELETE operation to `/api/v1/posts/actions/unlike`.
- [ ] For testing RESTful clients, use mock server. Use [MockWebServer](https://github.com/square/okhttp/tree/master/mockwebserver) JUnit rule for testing HTTP interactions.
- [ ] Learn how great REST APIs are designed. I refer to [Github REST API](https://developer.github.com/v3/) when in doubt. I find it the best designed REST API.

### [Code Review](https://www.atlassian.com/agile/code-reviews)

> ***Code reviews are about code not people. Don't take code criticism personally.***

- [ ] Are there any obvious logic errors in the code?
- [ ] Are unit tests written for the business logic?
- [ ] Does all the functional requirements met?
- [ ] Does the code conform to existing style guidelines?
- [ ] Propose better way to do certain tasks. It could be a library function that developer can use.

## Front-end

- [ ] Commit `yarn.lock` file
- [ ] Remove all `console.log` statements in the code.
- [ ] Use linter and integrate it with the build tool.
- [ ] Make sure there are no warnings and errors in the console.
- [ ] Test on all the four major browsers — Chrome, Firefox, IE, and Safari.
- [ ] Check spellings.
- [ ] Make sure grammar is correct in the messages.
- [ ] Add Google Analytics into your project.
- [ ] Use jQuery 3 instead of earlier versions of jQuery.
- [ ] Prefer Angular 4+ over Angular 1.x. 
- [ ] Don't use Bower. Use npm to manage client side dependencies.

## Website performance optimization

- [ ] Run [Lighthouse](https://developers.google.com/web/tools/lighthouse/) tool on your website.
- [ ] Go through [BrowserDiet](https://browserdiet.com/en/) guide.
- [ ] All my application web pages load under 3 seconds.

## License

- [ ] Make sure you do not violate 3rd-party dependencies licenses. Your can use [LicenseFinder](https://github.com/pivotal/LicenseFinder) to compare licenses against a user-defined whitelist.

-----------
You can follow me on twitter at [https://twitter.com/shekhargulati](https://twitter.com/shekhargulati) or email me at <shekhargulati84@gmail.com>. Also, you can read my blogs at [http://shekhargulati.com/](http://shekhargulati.com/)
