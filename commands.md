#Important Git Commands

### Begginer Level Commands

- `git init` -> it initialize a new gitt repository.What is a repository?It is a folder managed by git where we can track all the changes we are making in the project.

- `a new version` -> if we have to create a new version we have to create a new commit.
  initalialiy all file are untracked.

How can we tell git git that this file need to track
`git add index.js`

then we get changes to be commited
now we get know about files where you are doing code
and changes things

`git status`-> it will show track of your code

`git commit` -> will add whatever version of code with commit
suppose first version of code in commit.`git commit -m "first message"`

In short this will creates a new version based on your prev changes.

`git log` -> it will show all your commits with the id
the author ,mail date and time show

`cat index.js` -> will show code or content of that file

`git remote add origin (Your-Url of github which provided)` ->
it will add local machine file to github

`remote` -> something that not locally available
so,we want to add
`origin` -> remote repository short name
for that remote we name short as origin

after this code we have to write the code

want to do upload the changes

`git push origin master` ->push the code to master

`git clone` -> `repo clone to local machine`

How exactly git internally git store data?

internally git a <key,value> data store

`key` -> hash of the data we want to store (40 digit hexadecimal value)
(for same data thiss hash will be same)
`value` -> actual data (git stored the comprased data in a blob ,and some more meta data in the Header)

`https://developer.mozilla.org/en-US/docs/Web/API/Blob`

blob = big large object

`git add .`
`tree .git`

we can see that data as object 40 length hash

─ `24`
│   │   └── `3a7b5632e13b7b06d8fa7c952bb90e99f574f5`
│   ├── `70`
│   │   └── `2f4280cee76a8b022e896aedf2bad15b43726f`

`24` and `70` hash before 2 charcter which usse for that specific add (it's part of hash 2 charcter )

inside git content only stored once

How git handle directories?

`Tree` -> store information about directories & their content

`Tree` contents pointers to others blobs & trees

i have make 2 file test.js and test1.js if content is same for both then it will not create 2 objects only create object where data store for both.
`refer` same object

git internally does a lot of optimization, the object are store inn compresed form

it manly store data about the change & algorithmically shoes the file content change

very intersting command

`git cat-file <flag> <hash>`

using this you can see the type of the file and content of the file

`-p` -> print the content in the objects

`-r` -> type of the object

`git cat-file -t 243a7
blob`

`git cat-file -p 702f4
console.log("hello");`

`commit` -> object
every commit object point to a tree
the commit object has data of author & committer
data
message
parent commit

when you do commit and see you will find out that it is tree
`git cat-file -t 8f12d
tree(output)
`

`git cat-file -p 8f12d
040000 tree 88bf742839a63e153d7f67c0896568bb88a881f2	coding
100644 blob f5f7e7185b65def43a9bf882603f729123446968	commands.md
040000 tree b0d4a6557ac193f35307a77ee4a6ed14bebbe028	nothing
100644 blob 702f4280cee76a8b022e896aedf2bad15b43726f	test.js
100644 blob 702f4280cee76a8b022e896aedf2bad15b43726f	test1.js`

`commit of tree also so with which code for commit`

`git cat-file -p 1f0d9
tree 8f12d7500e6bd0d1dd4535bc1166632ed581885b
author codecare321 <codecare321@gmail.com> 1713685391 +0530
committer codecare321 <codecare321@gmail.com> 1713685391 +0530

First commit`

In a lot of company

when i want to change in old commit

there is command `git commit --amend`

even if you change the commit it will create the new commit because
when you add new commit it will add with time for that specific time when you are adding

`commits never change`

`never do force push on remote`

What is the content inside this HEAD?
it s HEAD POINTER
Current latest committ point

`git log --oneline` -> latest comment show

`1` -> working area

`2` -> staging

`3` -> Repo

#working area

-> the files which are not in staging area and maybe corrently not handled by git are in working area.

These files are also called as untracked files

if you want to see all branch right `git branch`

for deleting previous error for previous account.

To simplify and add into it, one can follow below simple steps:

Remove all GitHub entries from (Windows) Credential Manager
Set useHttpPath = true in Git global configuration
git config --global credential.useHttpPath true

You can validate this by checking

git config --global -e

This will create a different entry for each user account.

for new branches make use `git checkout -b Feature_1`

for checking code of main
we can do
`git checkout main`

`git log` -> check the commit

`git commit `-> in main
so whatever your last main and when you do new branch according to last main it will take code of that

for creating new branch you have to do `git checkout -b Feature_1(name of your branch)`

in github you are able to see only one branch main

can you figure out why?

you have never told github that you have new branch.

you can do this

`git push origin Feature_1`

the recommonded practice for industry is

Now,How can we merge the change?

Feature \_1 is done now this code need to merge in main branch

then first go to in master branch

`git checkout main`

`git merge Feature_1`

for your merge:

Very Very important Thing

when one of your teammate make changes suppose in master and you have make him as collabrotor so he add one file but in your local you dont aware of that code and you also making file for main

how can you get that your friend channges code?

so your local repo dont know about that file how you will get?

in this situation if you try to push the code it will not allow.

let s see

`git status`

`On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	algo.js
	commands.md`

git add ann commit will work

when i do `git push origin main`

`! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/codecare321/Branches_Demo.git'`

`
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref`

before we have to push the code

never do forcefully push if you do that then your team mate push will be vanished

viilation of everything softtware engineer tell

what use case you have to do?

we have to do all latest commit to be get as we do as collabrator

so what i can do?

`git pull origin main`

and those commit will be added

before the pull in your code if you have added anything in that you have to do merge otherwisse alsos it give problem

if you have 2 people in your team always do (as collabrator)

git add
git commit
git pull
then
git push

never do git push directiy

now let me make another teammate2.js which added by other

now i am add one file in my local

now i am doing git pull and somebody else added as team to code

now you do new_algo.js(from your local file you are trying to add)

so you have to add that and commit and thenn do `git pull origin main`
`git push origin main`

what is merge conflict?
2 or more people trying to do same code base same line code change try to do git push then it will conflict the code.

suppose you are pulling the code in test.js and when you do pull git reliaize that for both code for line number 4 are conflicting

you have to resolve the prolblem.

fix the conflict then merge it

`git branch` will show branch

we never do merge and push from feature branch

What is the correct way to do that?

`pull request`

it is extresmly wrong without feature reviwing push the code

github allow to put the review that without allow it can not be push the code

create a pull request
