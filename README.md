# git_tutorial repository 

git and github basic lessons
1. coloning
to clone the repository we need to use git clone command 
#command is given below 
git clone https://github.com/nahidul007/git_tutorial.git
#
2.change or editing the file or folder, using nano or mkdir
3.Add this changing or editing file or folder name 
git add README.md(which file you want to update or upload) 
4. Know the status of updated file 
#git status (to identify the current file is update or modified then need to commit )
5. git commit -m "here your updated module name (your wish provide name ) you provide sothat next time you easily know what you change "
6. git push origin main 
   a. first you provide your username 
   b. password
if it was not working then you create token form github then use this token . I provide  a demo  example in below 

git remote set -url origin https:// gittoken @github.com/nahidul007/git_tutorial
if you provide this format in your terminal then you will easily upload file and folder next time 
