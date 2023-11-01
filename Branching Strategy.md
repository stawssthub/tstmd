##  BRANCHING STRATEGY

**ASSUMPTIONS:**<br>
1.  you are not maintaining the multiple    releases    of  the same  code    or  database, will    have    the same    database    on  different   environments.<br>

2.  will    have    more    than    one person  for every   part    of  code    to  review  and approve,    which   means   if  one person  can commit  changes and another person  can always  review the  code   and approve it,  if  that    is  acceptable.<br>

3.  We  can use automation  and start   automatic   deployments on  each    environments    in  sequence.<br>

<br>

#   MAIN    BRANCH  DEPLOYMENTS

1.  In  "main"    branch  deployement we    only    consider    "main"    branch    to  deploy  the code    into    all environments,   and we  don't   need    multiple    vesrion of  code    to  different   environments.<br>
we  have    to  create   "feature" branch  and as  part    of    feture  branch  if  we  make    any changes that    are needed,    but those   branches    always  be merged back  into  "main"    branch, now main    has to  be  very    stable, and it  is  suppose to  be  a   golden  branch.<br>

2.  Steps to  Clone   the Project Code    and Push    to  Remote  Repository  in GitHub:
    1.   Clone respective   repository  from    GitHub  to  local   computer(VDI).  from    repository  page    on  GitHub  click   the green   button  labeled clone   or  download    and "clone  with    HTTPS'  section and copy    the repository **url**.<br>
    

    2.  Open  up  a   git bash    terminal  in  local   computer(VDI)   and navigate    to  the directory   where   we  want    to  clone   the repository  and run the git clone   command with the    address of  respository with  the following   command.<br>

    `git clone https://name-of-the-repository-link`<br>

    ![Poll  Mockup](https://github.com/stawssthub/tstmd/blob/main/Clone_Repo.PNG)

