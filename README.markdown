# README - Spring RTS Maven support files

## Intro

These files are used by different projects related to the Spring RTS game engine
which are based on the Maven build system. This makes up mostly Java projects.

These files are useless by themselfs, and their main purpose is to unify
and simplify Java based projects related to Spring RTS.

Projects that may use these files:
* SpringLS
* JUnitsync
* Java-AIInterface
* JavaOO-AIWrapper
* Java based Skirmish AIs


## Use

Configure either of the Maven projects contianed in this repo
as the parent of your own projects.


## Release a SNAPSHOT

To release a development version to the Sonatype snapshot repository only:

		mvn clean deploy


## Release

### Prepare "target/" for the release process

	mvn release:clean

### Prepare the release
* asks for the release and new snapshot versions to use (for all modules)
* packages
* signs with GPG
* commits
* tags
* pushes to origin

		mvn release:prepare

### Perform the release
* checks-out the release tag
* builds
* deploy into sonatype staging repository

		mvn release:perform

### Promote it on Maven
Moves it from the sonatype staging to the main sonatype repo.

1. using the Nexus staging plugin:

		mvn nexus:staging-close
		mvn nexus:staging-release

2. ... alternatively, using the web-interface:
	* firefox https://oss.sonatype.org
	* login
	* got to the "Staging Repositories" tab
	* select "com.springrts..."
	* "Close" it
	* select "com.springrts..." again
	* "Release" it

