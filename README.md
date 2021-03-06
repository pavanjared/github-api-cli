# GitHub API Command Line Interface (test)
This is a command line interface (CLI) written in bash to test out working with GitHub's API on public repos. Given commands, it will print out *n* issues or pulls ordered by their comment activity. Its functionality is currently limited and is meant for a proof of concept.

It could also use some more error handling (like Developer Over Limit and repo "Not Found" catchers)

## Dependencies
You will need jq installed on your machine in order to operate this CLI.
### OSX
```bash
brew install jq
```
If you don't have brew installed, then first run
```bash
ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
```
### Linux
```bash
git clone https://github.com/stedolan/jq.git
cd jq
autoreconf -i
./configure
make
sudo make install
```

## Setup
```bash
git clone https://github.com/pavanjared/github-api-cli.git && cd github-api-cli
```

## Usage
```bash
Usage: ./github-api-cli.sh [mode] [org] [repo] [output count]
mode: there are two modes [issues|pulls]
org: specify an org
repo: specify a public repo
output count: specify how many lines of output sans header
```

## Examples
```bash
➜ ./github-api-cli.sh pulls WhiteHouse petitions 3
Comments  PR Title
3         "Update is_profane.module"
3         "Refactoring and new generator to aid in responses."
2         "Fixes to work on localhost without special access."
```
```bash
➜ ./github-api-cli.sh issues github gitignore 10
Comments  Issue Title
4         "[ObjC][Swift] Ignore Xcode SCM blueprint files"
4         "Add trailing slash to .sass-cache"
3         "Add CMakeScripts directory"
2         "include preamble files generated by mylatexformat package"
2         "Sonar .gitignore file"
2         "Removed the extra \"/\" from the directory ignore."
2         "Remove Meteor.gitignore"
2         "Ignore temp Hypothesis test things"
2         "First .gitignore for Stata files"
2         "Added gitignore for Biicode - C and C++ Dependency Manager"
```
