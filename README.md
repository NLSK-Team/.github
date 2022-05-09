# Git Procedures
In order to assure maximum work flow and proper backups of data, please adhear to these git procedures

Branches:
Branches are used to split code of the main branch.
Consistently every project should have at least 2 branches
-Main (current build used by platform and loader)
-Beta (Next working build for beta users

Commits:
Developers on the project should be commiting to branches at least once every 3 hours of working
to have historical records of working or almost working versions.

Commits that are not working and are not from either of the two main working branches above should be commited 
to a new branch that is titles after the feature or main feature they are working on, and on a working iteraion of that branch should be join with beta
then after testing staged onto the main branch.

Tags:
Tags will be used to mark known working builds of different features and build versions
For example if you merge a branch with master or beta, it should then be tagged with the feature name that was added or modifed in that branch with todays date

Issues:
All bugs or additional features should be added to the issues tab and reported with as much detail as possible as well as the name of the user who found the bug
This will allow easer tracking and fixing of various issues with the products






