Amazing Tutorial http://pcottle.github.io/learnGitBranching/
GIT Graph tree on terminal
http://stackoverflow.com/questions/1064361/unable-to-show-a-git-tree-in-terminal
http://gitready.com/intermediate/2009/01/26/text-based-graph.html
Amazing wall print http://www.git-tower.com/blog/git-cheat-sheet-detail/

### Git ignore Sample

```
# .gitignore file for java project
########################### Java
/target/*.*
/target/*
/target
/bin
/build
*.class
########################### Gradle
/gradle
/gradle/*.*
/gradle/*
/.gradle
########################### Packages
*.jar
*.war
*.ear
 
########################### Linux
*~
*.lock
*.DS_Store
*.swp
*.out
########################### Windows
Thumbs.db
 
########################### Mac OS X
.DS_Store
._*
########################### Netbeans ignore personal stuff 
nbproject/private/

```

### Change Git History

```
git rebase -i HEAD~2
git commit --amend
git rebase --continue
git log
git push --force origin SRCH-499-RichTypeDecoders
```
