# :ballot_box_with_check: building-java-web-apps-checklist
This repository shares a checklist that I use for building web applications in Java+ Angular/React.

## :beginner: Before you start development

- [ ] Take architectural decisions.
      - [ ] Finalize tech stack
- [ ] Create a multi-module Maven or Gradle project for your development. Start with two modules — `backend` and `frontend`.  You can refer to [spring-boot-react-maven-starter](https://github.com/shekhargulati/spring-boot-react-maven-starter) for inspiration.
      1. `backend`: This contains Java code of the application.
      2. `frontend`: This contains all react JavaScript code of the application.
- [ ] You should use [Maven](https://github.com/takari/maven-wrapper) or [Gradle](https://docs.gradle.org/current/userguide/gradle_wrapper.html) wrapper scripts so that a new developer do not need to install Maven or Gradle on their machine before executing the build.
- [ ] Build project as a single jar/war using a single command i.e. if I am using Maven as my build tool then I should be able to run `./mvnw clean install` in the project root to build the executable.
- [ ] Set up CI server and make sure it can build the project as a single executable.
- [ ] Fix standup time and make sure it works for everyone.
- [ ] Finalise your sprint duration. 
- [ ] Finalise your testing strategy both manual and automated.
- [ ] Each team member should come up with their learning goal.

## :computer: During development

- [ ] Git

      - [ ] Work on feature branches.
      - [ ] Branch out from `develop` branch
      - [ ] Never push to `master` or `develop`. Make a pull request.
      - [ ] Create PR on the `develop` branch and once it is tested then only merge to master. You can use different strategy like merge to `master` once sprint finishes.
      - [ ] Delete local and remote branches after merging. You can automate this process as well.
      - [ ] Before raising PR, run the build locally and make sure all tests pass.
      - [ ] Use `.gitignore` file.
      - [ ] Protect your `master` branch.
      - [ ] Never commit binary files to Git.
      - [ ] Write meaningful Git commit messages. [Read Chris Beam post on it](https://chris.beams.io/posts/git-commit/).
      - [ ] Feature branches should be short lived.
- [ ] CI

      - [ ] Every code committed to version control system mainline should trigger a continuous integration job that runs on the integration server.

      - [ ] Continuous integration job should build the project and run all unit test cases. It should happen on each code commit to mainline.

      - [ ] Fix broken builds immediately. CI server should always be in healthy green state.

      - [ ] Make CI server visible and transparent to whole team.

      - [ ] Maintain build jobs as code use `Jenkinsfile` if you are using Jenkins

      - [ ] You should be able to create build jobs on a new CI server using code.

      - [ ] Use pull request builder to build the project when pull request is raised.

      - [ ] ​
- [ ] Documentation
      - [ ] Create `README.md` file in root of your project and keep it updated. The README file should have following:
            - [ ] Couple of lines describing purpose of the project
            - [ ] instruction to grab the latest code and detailed instructions to build it
            - [ ] Instructions to run the project on local machine
            - [ ] Link to Continuous integration server
            - [ ] Instruction to do any setup required for the project
            - [ ] Instruction to grab project documentation
            - [ ] Any other relevant information that can help a new developer get started with the project
- [ ] Code style
      - [ ] Use check style in your project. Make sure you it is integrated with the build
- [ ] Testing

      - [ ] Write one automated functional test per user story.
      - [ ] Cover business logic with unit/Integration tests.
      - [ ] Understand different between unit testing and integration testing.
      - [ ] Use consistent names for tests. I prefer to use `*Tests` as suffix for my tests.
      - [ ] Use consistent naming strategy for tests like `shouldRegisterNewUser` or `registerNewUser` or `should_register_new_user`
- [ ] Dependencies

      - [ ] Add a new dependency to the project after discussing with the team.
      - [ ] Use [Snyk](https://snyk.io/) to check security vulnerabilities.
      - [ ] Don't add dependency for each problem you face. First check if you already have some dependency that solves the problem.
- [ ] Learning

      - [ ] Spend one hour on learning every day.
      - [ ] Give XKE.
      - [ ] Write blog.
- [ ] Naming

      - [ ] Think and discuss with team before choosing a name for public member.
      - [ ] Java and JavaScript use PascalCase for classes, interfaces, enums, annotations.
      - [ ] Java and JavaScript use camelCase for methods and variables.
- [ ] Exception handling

      - [ ] Catch any checked exception thrown by the code.

      - [ ] Convert checked exception to unchecked exception.

      - [ ] Throw the unchecked exception. Unchecked exception could be custom or plain RuntimeException

      - [ ] Always use two arguments constructor of RuntimeException. The first take a message, second is the actual exception

      - [ ] Catch all exceptions thrown by code in your Controller or Resource classes

      - [ ] Log exceptions only in the Controller or Resource classes

      - [ ] Log both the message and exception. If using slf4j, use log.error(“message”,e)
- [ ] Logging
      - [ ] Use slf4j with logback for logging.
- [ ] REST API design