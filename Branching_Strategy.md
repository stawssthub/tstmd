##  BRANCHING STRATEGY

**ASSUMPTIONS:**<br>
1.  We  are not maintaining the multiple    releases    of  the same  code    or  database, will    have    the same    database    on  different   environments.<br>

2.  will    have    more    than    one person  for every   part    of  code    to  review  and approve,    which   means   if  one person  can commit  changes and another person  can always  review the  code   and approve it,  if  that    is  acceptable.<br>

3.  We  can use automation  and start   automatic   deployments on  each    environments    in  sequence.<br>

<br>

**MAIN    BRANCH  DEPLOYMENTS:**<br>

1.  In  "main    branch"  deployement we    only    consider    "main    branch"    to  deploy  the code    into    all environments,   and we  don't   need    multiple    vesrion of  code    to  different   environments.<br>
we  have    to  create   "feature branch"  and as  part    of    feture  branch  if  we  make    any changes that    are needed,    but those   branches    always  be merged back  into  "main    branch", now main    has to  be  very    stable, and it  is  suppose to  be  a   golden  branch.<br>

2.  Steps to  Clone   the Project Code    and Push    to  Remote  Repository  in GitHub:
    1.   Clone respective   repository  from    GitHub  to  local   computer(VDI).  from    repository  page    on  GitHub  click   the green   button  labeled clone   or  download    and clone  with    HTTPS    and copy    the repository **url**.<br>
    

    2.  Open  up  a   git bash    terminal  in  local   computer(VDI)   and navigate    to  the directory   where   we  want    to  clone   the repository  and run the git clone   command with the    address of  respository with  the following   command.<br>

        `git clone https://name-of-the-repository-link`<br>
    
    3.  Next  we would have to   change  the directory   to repository folder    where  it  is  cloned.<b>

        `cd <repo_name>`<br>

    4.   By  default we would be  on  "main branch"  when   we  clone   the repositrory, so  we  need to be create  a   new branch called  "feature    branch"    and checkout    to  that    branch. then we  have    to  add the code/develop    the code    into    the project folders/files    based   on  user    stories.   we  can use following   command.<br>
    

          `git checkout -b feature`<br>
    
            **Note:**   The moment we created   the new branch  it  will    be  having  the exact   copy    of  main    branch.

    5.  Next  open    up  code    editor  like    VS  code    and writ  the code/database    in  the files    and save    the changes,    once    we  are ok  with    the changes which   are saved,  then    go back to  terminal    and run the following   commands.<br>

        `git status`    // To  keep track   of  changes.<br>
        `git add file-name `   // To add the changes    in  single  file.<br>
        or<br>
        `git add .` // to add   the changes in  multiple    files.<br>
        `git commit -m "commit message”`  //To commit all changes.<br />

    6.  So    far   we  have    only    modified    our local   copy    of  the respository.    To  add the changes to  git repo    files   on  local   computer    to  the version of  remote  repository  on  GitHub  we  can push    chnages with  the following   command.<br>

        `git push -u origin feature`<br>

        *Flow Chart:*

        ```mermaid
            graph TD;
            A[Remote Repository] -->| clone_repo_to_local_| B(git clone https://name-of-the-repository-link_);
            B -->|Change_to_directory_| C[cd repo name_];
            C -->|Creata_&_checkout_to_feature_branch_| D[git checkout -b feature_];
            D -->|Add_code_to_files_&_check_status_| E[git status];
            E -->|Add_files_to_staging_| F[git add file-name or git add ._];
            F -->|Commit_changes_to_staging_| G[git commit -m commit message_];
            G -->|Push_feature_branch_changes_to_remote_repo_| H[git push -u origin feature];
        ```
    <br>

    7.  After we  have    pushed  new   changes,    visit   the remote  repository  on  GitHub  and notice  that    changes are reflected   there,  then    we  need    to  create  a   pull    request form    “feature branch to  “main branch”    by  adding required Reviewers .<br>
        -  To  creat   a    pull    request,    navigate    to  the repository  page    and click   on  pull    requests.<br>

        -   then    click   "New pull    requests"  or  we  can identify    the pop-up  message like "Compare   &   pull    requests" when  we  pushed  changes,    either  way we can  do, so  click   on  "Compare   &   pull    requests".<br>

        -   As  part of this PR we  will    see "Base   branch is   main    and Compare branch is   feature",   then    we  have    to  provide "Title  Name"   and add a   description,    next    click   on  create  pullrequest.<br>

        -   when we created the pull    request it  will    show    the difference  between main branch and current working branch  the new chages  that    we  made.<br>

        -   if you  want    to  see changes what    we  have    done    on working  branch  in  GitHub, select  respective  branch  and click   on  recent  "Commit  ID", we would be   able    to  see what    changes have    been    made    in  that    "Commit ID".<br>

        -   based   on  "Commit ID",    reviewer    will    verify  the chamges and approve them if changes are ok, then    check   the viewed box, and he  can approve changes or  request for specific    changes.<br>

        -   if  reviewer request    for changes as  part    of  PR, that    PR  can not be  merged. and those   changes are not going   to  the main    branch.<br>

        -   if  PR  approved,   then    only    it  will    be  ready   for merge,  once    it  is  ready   for merge   we  can click   on  "merge   pull    request".<br>

            **Note:**   If  developers  working at  the same    time on the same    code    by  creating    their   own branches,   and if  they    pushed    changes by  creating    pull    request they  might   get branch  conflicts   while   creating    pull    requests.   so  who ever    second  person  coming  in  they    will    have    to  get the first   person  changes from    the "main    branch" before  they    merge   to  main.

            <br>

            *Flow   Chart:*<br>
            ```mermaid
                    graph TD;
                    A[Pull Requests_] -->|create_pull_request_| B[New Pull request];
                    B -->|Compare changes_| C[Base:main and compare:feature_];
                    C -->|Able_to_merge_ok_| D[create pull requests];
                    D -->|Add_tile_&_description_| E[creat pull request];
                    E --> F[click on file _changed_];
                    F -->|Review_changes_| G[if changes ok_];
                    G -->|Check_the_box_for_Viewed_ | H[click on review changes_];
                    H -->|Leave_a_comment_| I[submit review];
                    I --> J[click on merge pull requests_];
                    J --> K[click on conirm merge_];
            ```

    8.  If  another developer   also working on other   branch  he  might   have    to  pull    the latest  changes to  his current working branch  from    the "main    branch",   we  can use following   command to  pull    the changes.<br>

        `git pull  origin main`<br>

    9.  Then    check   the status  of  latest  changes that    have    made    in  "main" using    git statu   command and do  repeat  the number   5,6 &   8   steps.<br>

        `git status` <br>

        <br>
   
        *Flow   Chart:*.<br>


        ```mermaid
            graph TD;
            A[Pull updates of main from remote repo_] -->|pull_updates_to_local_repo_| B[git pull  origin main_];
            B -->|Check_status_for_changes_| C[git status];
            C -->|Creata_&_checkout_to_feature_branch_| D[git checkout -b feature_];
            D -->|Add_code_to_files_&_check_status_| E[git status];
            E -->|Add_files_to_staging_| F[git add file-name or git add ._];
            F -->|Commit_changes_to_staging_| G[git commit -m commit message_];
            G -->|Push_feature_branch_changes_to_remote_repo_| H[git push -u origin feature];
        ```
3.  Once    we  completed    the pull    request,    the Workflow    will    be  trigger,    that    we  can see in  Action  tab. and   we  will    be  able    to  see the build/workflow  number, and if  we  click   on that workflow    we  can see the deployment  process for all environments    in  order.<br>

4.  as  soon    as  merge   completed   changes are pushed  to  the main    branch  and CI/CD   will    be  triggered.  first   changes will    be  deployed    into    the "Dev environment",    then    changes deployed    to  "test environment" if Dev passed, and then    changes deployed    to  "uat environment" if  tes passed    and finally changes deployed    to  Prod    environment by  enabling    the approvals based on  rules.<br>

    means,  we  will    enable  the some one as reviewers   (approvals)   who is  responsible for production  deployment  and  they    can review  and approve the deployment job  to  deploy  the changes to  Prod.if they    reject  changes will    not be  deployed    to  prod.<br>

    **Note:**   if  any deployment  job failed,  the deployment  job for the next    stage   will    not be  started.    example,    if  deployment  on  test    environment is  failed  the workflow    job will    be  stopped and it  will    not start   the Uat environment.<br>

    *Flow   Chart:*

    ```mermaid
            graph LR;
            PR -->| merged -- |A[main];
            A -->| Triggered workflow -- |B[deploy_to_dev-];
            B -->| if_dev_success -- |C[deploy_to_test-];
            C -->| if_test_succes -- |D[deploy_to_uat-];
            D -->| if_uat_success -- | E[review_&_approve-];
            E --> F[deploy_to_Prod-]
    ```
    <br>

       ```mermaid
            graph LR;
            PR -->| merged -- |A[main];
            A -->| Triggered workflow -- |B[deploy_to_dev-];
            B -->| if_dev_success -- |C[deploy_to_test-];
            C -->| if_test_failed -- |D[stop_deploy_to_uat-];
            D -->| if_uat_skipped -- | E[stop_deploy_to_prod-];
    ```

5.  steps   to  add the environments    in GitHub.<br>

    -   On  GitHub  navigate    to  the main    page    of  the repository.<br>

    -   Under   your    repository  name,   click   Settings.   If  you cannot  see the "Settings"  tab select  the dropdown    menu,   then    click   Settings.<br>
    
    -   Click   New environment.<br>

    -   Then    enter   a   name    for the environment,    then    click   Configure   environment.    environment names   are not case    sensitive.  An  environment name    may not exceed  255 characters  and must    be  unique  within  the repository.<br>

    -   Optionally, we  specify people  or  teams   that    must    approve workflow    jobs    that    use this    environment.<br>

    -   To  add reviewers:<br>

        1.  Select  Required    reviewers.<br>
        2.  Enter   up  to  6   people  or  teams.  Only    one of  the required    reviewers   needs   to  approve the job for it  to  proceed.<br>
        3.  Optionally, to  prevent users   from    approving   workflows   runs    that    they    triggered,  select  Prevent self-review.<br>
        4.  Click   Save    protection  rules.<br>


<br>


**PROS    and CONS  of  MAIN    BRANCH  DEPLOYMENTS:**<br>

**pros:**<b>

1.  Frequent    releases    with    short   production  cycles.<br>

2.  Automation take care    of  deployments to  higher  environments.<br>

3.  Fast    feedback    loops   if  Something   fails.<br>

**Cons:**<br>

1.  Timed   releases    to  environments    is  not possible.<br>

2.  Rleases are pushed  in  order   unless  failures    block   a   deploy.<br>

3.  Team    doesn't have    much    control on  deploys to  higher  environments    beyond  merging the PR.<br>
4.  Any fix has to  go  through all environments.<br>