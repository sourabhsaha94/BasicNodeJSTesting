# Summarize the main purpose of the tool?

Continuous Integration (CI) testing is a software development practice where code changes are immediately tested with the entire codebase every time that new code is committed and merged into the source code. The goal of CI is to provide rapid feedback so that if bugs are introduced into the code base, they can be identified and corrected as soon as possible.

With cloud based continuous integration services, the actual test process is moved from the local development environment onto cloud servers so that developers don't need to sit through the long process of running tests locally. As code changes are committed to the repository, the cloud CI services spin up resources to run the test suite and check the new code. When the automated test suite is completely processed by the cloud CI service, statistics are passed back as to what portions of the code in the build passed tests and what failed.

Coveralls takes the build data from whichever CI service your project uses, parses it, and provides constant updates and statistics on your projects' code coverage to show you how coverage has changed with the new build, and what isn't covered by tests. Coveralls even breaks down the test coverage on a file by file basis. You can see the relevant coverage, covered and missed lines, and the hits per line for each file, as well as quickly browse through individuals files that have changed in a new commit, and see exactly what changed in the build coverage.

# Relate the tool to previously presented articles?

# Present the tool in a clear, logical manner?

# Critique the tool and present possible limitations?

# Justify his or her own opinions about the tool?

# Personalize the topic, such as by bringing in their own experiences?
