# Pushing the changes you made to Github

Once you are done with all of the changes that have made to your website, open up your command line in your VSCode by pressing `Ctrl + ~`. Enter the following commands into the command line one by one, and press enter after each of them to execute the command.

```shell
git add -A
```
This will add all the new files you have added to your codebase into the commit.

```shell
git commit -am "A short description of your commit"
```
This will commit all the changes that you have made to the codebase. Replace the text to what you want so that you can easily keep track of the change you have made.

```shell
git push origin
```
This will push the commit that you have made to Github, and automatically reflect the changes to your website for you.It should take around 1 minute or less to see the new change being reflected on your website.
