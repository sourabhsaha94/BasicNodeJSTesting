# Summarize the main purpose of the tool?

Continuous Integration (CI) testing is a software development practice where code changes are immediately tested with the entire codebase every time that new code is committed and merged into the source code. The goal of CI is to provide rapid feedback so that if bugs are introduced into the code base, they can be identified and corrected as soon as possible.

With cloud based continuous integration services, the actual test process is moved from the local development environment onto cloud servers so that developers don't need to sit through the long process of running tests locally. As code changes are committed to the repository, the cloud CI services spin up resources to run the test suite and check the new code. When the automated test suite is completely processed by the cloud CI service, statistics are passed back as to what portions of the code in the build passed tests and what failed.

Coveralls takes the build data from whichever CI service your project uses, parses it, and provides constant updates and statistics on your projects' code coverage to show you how coverage has changed with the new build, and what isn't covered by tests. Coveralls even breaks down the test coverage on a file by file basis. You can see the relevant coverage, covered and missed lines, and the hits per line for each file, as well as quickly browse through individuals files that have changed in a new commit, and see exactly what changed in the build coverage.

# Relate the tool to previously presented articles?

# Present the tool in a clear, logical manner?

# Critique the tool and present possible limitations?

# Justify his or her own opinions about the tool?

# Personalize the topic, such as by bringing in their own experiences?


# Setup instructions

## Relevant files

* [package.json](package.json)
* [Code to test](app/converter.js)
* [Code with tests](test/converter.js)
* [Travis yml](.travis.yml)

## 1. Tests that cover code
* Before you begin to generate coverage reports, make sure you have tests that run on a code snippet
* We have used [mocha](https://mochajs.org/) and [chai](http://www.chaijs.com/) to create simple tests for our code. For example:
```
describe("Temperature converter",function(){
  describe("C to F conversion",function(){
    it("converts c to f",function(){
      var f = converter.celsiusToFarenheit(30);
      expect(f).to.equal(86);
    });
  });
  describe("F to C conversion",function(){
    it("converts f to c",function(){
      var c = converter.farenheitToCelsius(50);
      expect(c).to.equal(10);
    });
  });
});
```

## 2. Install the required packages
* Since, we are testing javascript code, we used npm and nodejs for our application. Npm uses [package.json](package.json) file
* The packages that were using are:
```
npm install --save-dev nyc mocha chai coveralls
```

## 3. Update package.json 
* The [package.json](package.json) file must have the following line in the "scripts" section:
```
"scripts": {
    "test": "nyc --reporter=html --reporter=text ./node_modules/.bin/mocha",
    "coverage":"nyc report --reporter=text-lcov | coveralls"
  }
```

## 4. Connect Github repository to Coveralls
* [Coveralls.io](https://coveralls.io/) works with Github repositories when you link your Github username to the tool
* Once your account is linked and you're repositories have been synced, you can add the desired repository by flicking a switch at [https://coveralls.io/repos/new](https://coveralls.io/repos/new)
* There are two ways with which you can send coverage information to coveralls:
  * Using a CI tool like Travis CI, you need to set up your repository with Travis and have `after_success: npm run coverage` in the `.travis.yml` file
  * Using the command line, you need to add your repo token to the environment variables using `export COVERALLS_REPO_TOKEN=xxxxxxxxxxxxxxxxxxxxxxxxxxx`. The repo token can be found when you go your repo url in coveralls, for example `https://coveralls.io/github/sourabhsaha94/BasicNodeJSTesting`

## 5. Checking the coverage
* After the repository has been set up, and it has been linked with Travis or you're command line, you can go ahead and push the tests to your repository.
* If you've used Travis, then the coverage information will get automatically on the site displayed once you're build is complete.
* If you've added the COVERALLS_REPO_TOKEN manually into you're environment variables, running `npm test` and then `npm run coverage` will send your coverage information to the website.

[](!coverage.png)

# Screencast

