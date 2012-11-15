#My git tricks

In this project I keep updated my local .gitcontig file to share it with you, as well as some of my hooks.
And I also keep updated this README to explain in detail every configuration I have, just in case some of them are useful to you.


##How to install

If you find my configurations useful, you just need to copy the file I share as ".gitconfig" to your home folder.
Also, if any of my hooks is useful for you, copy it to the proper folder of your project.

Be careful! As noted in the comments of the .gitconfig, some configurations are specific to me (my name, email, ...) and you should take only those that you understand and change them if needed to fit you.


##Aliases

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
