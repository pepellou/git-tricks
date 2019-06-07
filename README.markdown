# My git tricks

In this project I keep updated my local .gitcontig file to share it with you, as well as some of my hooks.
And I also keep updated this README to explain in detail every configuration I have, just in case some of them are useful to you.


## How to install

If you find my configurations useful, you just need to copy the file I share as ".gitconfig" to your home folder.
Also, if any of my hooks is useful for you, copy it to the proper folder of your project.

Be careful! As noted in the comments of the .gitconfig, some configurations are specific to me (my name, email, ...) and you should take only those that you understand and change them if needed to fit you.


## Aliases

### 'Work on' a specific commit

I created the alias 'workon' to work on the files related to a specific commit:

	workon = !sh -c 'vi -o `git show --pretty=\"format:\" --name-only $1 | tail -n +2 | xargs`' -

Of course you can replace vi with your favourite editor.
    
	Usage:
		git workon
		git workon master
		git workon HEAD
		git workon <commit-num>
		git workon <branch-name>

If you don't specify a commit, the last one is selected.

### Run tests

For me it's important to run the tests for a project while working on it. For that purpose I created specific aliases to run them with phpunit (which is my tool for running tests since my major work is in PHP):

	test = !sh -c \"phpunit --colors test/\"

That way, if you need a long command for running tests you can alias it to "git test". The above example shows how to run tests with phpunit producing a colored output.

Another interesting feature you can need is to separately run the tests to analyze the results for each of them. For instance, since phpunit only gives a final summary you can run each test separately to obtain info about timing and memory for each test:

	tests = "!sh -c \"for file in test/*Test.php; do echo \\$file:; phpunit \\$file > results34fu35g.test; grep -v \\\"^$\\\" results34fu35g.test | grep -v Bergmann; rm results34fu35g.test; done\""

It's a quick&dirt implementation, but that's the idea and it works.

## Rebase by default

For me it's important rebasing branches instead of merging them, specially when pulling work from other people, for a best code integration. For that purpose, we can prevent "git pull" from automatic merging by forcing "rebase" in the branches we specify:

	[branch "master"]
		rebase = true

Additionally, we can force it for every new branch:

	[branch]
		autosetuprebase = always

