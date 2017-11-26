
This fork of synergy is created to build on Linux Ubuntu only


# Compile

Synergy compiles with cmake.

## Dependencies

You need git, g++, cmake, and a few libs.

	sudo aptitude install git cmake gcc g++ libxtst-dev libcurl4-openssl-dev

The source has 3 zip files that need to be expaneded for the project to compile.

This is handled in the ./compile in this fork, essentially this is what it does.


	unzip ext/cryptopp562.zip -d ext/cryptopp562
	unzip ext/gmock-1.6.0.zip -d ext/gmock-1.6.0
	unzip ext/gtest-1.6.0.zip -d ext/gtest-1.6.0


## Compile

	./configure
	make
	sudo ./install    # N.B. **./**install

## Clean

	git reset --hard
	git clean -f -d

