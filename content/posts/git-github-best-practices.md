+++
title = 'Version Control Best Practices'
date = 2024-10-12T00:45:42+05:30
description = "Best practices around using the version control softwares like git"
summary = "Git Best Practices learnt so far in the field."
draft = false
tags = ["git", "best-practices"]

showToc = true
TocOpen = false
hidemeta = false
comments = false

disableHLJS = true # to disable highlightjs
disableShare = false
hideSummary = false

searchHidden = false
ShowReadingTime = true
ShowBreadCrumbs = true
ShowPostNavLinks = true
ShowWordCount = true
ShowRssButtonInSectionTermList = true
UseHugoToc = true
+++

## Why?

In a single line: It will make the your and your teammates' life easier.


### Disclaimer

1. Many people have written on this topic. I would present my take based on the experiences I had so far. So by all means, this is not an exhaustive list. Feel free to have a discussion about this in the [issues]({{< param "GlobalValues.repository-management.blog-github-issues-url" >}}) / [discussions]({{< param "GlobalValues.repository-management.blog-github-discussions-url" >}}) sections.

2. I made many mistakes with these practices and am still learning.

3. This is aimed at the devs who are joining the workforce for the first time and for the seasoned devs who might like to have a refresher.

## Best Practices

There are some generic suggestion that would improve the workflow drastically

1. make sure to use the vendor specific features like Labels & Project (GH) and Milestones (GL) Use Case:
    1. One of the places I am getting to use GitHub Labels is to have the End-of-Quarter or End-of-Month deployments tracking of PRs / Issues.
    2. Labels also come in handy when you need to filter the PRs that are under review and the ones that needs to be merged.
    3. Another use case is when we need to group the PRs based on functionality we are implementing which is distributed amongst different developers and need to be merged all to get the feature to work in your internal environment.
1. If you are on *nix system and use the ZSH, then definitely try the omz's git plugin. Aliases are a game changer.
        <!-- Some of my most used aliases:
        1. gc: git commit
        1. gp: git push
        1. gl: git pull
        1. gco: git checkout
        1. gcb: git checkout -b
        1. gd: git diff
        1. gds: git diff --staged
        1.
        1. glgga: git log --graph --decorate --all
        grh: git reset
        grev: git revert
        https://github.com/ohmyzsh/ohmyzsh/blob/master/plugins/git/git.plugin.zsh -->
1. If the changes that you are planning are huge. Raise a set of [stacked PR/MRs](https://graphite.dev/blog/stacked-prs). Not only it will help you manage the changes, but it will also make your reviewers not hate you. Use tools like [git-machete](https://github.com/VirtusLab/git-machete) to track these if the Centralized VCS does not provide this.

## 1. Writing Commits
### Generic suggestion
1. **Keep you commit size small.**

The whole point of having the commits (ie snapshots of your code) is so that you can reference it and revert (if needed) in later point of time. But if you have a commit that has changes in 10 files or a logically complex change, then it become challenging.

2. **Avoid amending comments.**

Amending comments to correct the title, description, or the file changes, is not usually a good practice.
Avoid as much as possible.

### Commit Title and description

1. **Have the commit message in Imperative (commanding) tone.**

    Reason: **Git itself uses the imperative whenever it creates a commit on your behalf.** [[2]]({{< relref "#references" >}})

    Eg:
    1. *Add input validation for registration API*
    2. *Bump minor version from v1.2.3 to 1.3.0*

    Ideally a commit message should be 50 character long. This is because when you log (`git log`), long commits title gets truncated, loosing the context.


    Commit message (in case of larger/important commits) should explain the changes in multiple paragraphs.

    eg:
    ```
    feat: Add input validation for registration API

    Adds rules for validating registrations of devices based on the validator rules defined in document: <link>. This prevents ...

    The changes also updates validators in corresponding DB models.
    ```

    Further resources to check out:
    1. [How to write useful commit messages](https://dev.to/jacobherrington/how-to-write-useful-commit-messages-my-commit-message-template-20n9)
    1. [FreeCodeCamp: How to write better commit messages](https://www.freecodecamp.org/news/how-to-write-better-git-commit-messages/)


2. **Make sure to have the correct prefix in Git Commits.**

    Some of the very frequently used prefixes in the commits are:
    1. *update*: when there is an update in the functionality
    1. *chore*: changes that does not changes functionality
    1. *feat*: when new functionality is added
    1. *docs*: updating documentation
    1. *fix*: bug fixes
    1. *style*: linting and code style commits
    1. *test*: testing code/scripts/scenario changes
    1. *ci*: ci/cd pipeline updates
    1. *perf*: performance related changes
    1. *refactor*: code refactors
    1. *revert*: revert commits or cherry picking revert commits

    These can vary based on team but above are the general prefix that are used. [[5] [6] [7]]({{< relref "#references" >}})

    So, ideally commit message would be:
    ```
    feat(license-registration): Add input validation
    ```
    or
    ```
    feat: Add input validation for registration API
    ```

### Commit Signing

Always sign the commits. This verifies that a commit is done by the author and no one else (remember commits can be amended to change the author as well).

Follow the guide by [GitHub - Commit Signing](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits) or [GitLab - Commit Signing](https://docs.gitlab.com/ee/user/project/repository/signed_commits/) and [FreeCodeCamp - What is commit signing in Git?](https://www.freecodecamp.org/news/what-is-commit-signing-in-git/).

## 2. Branches

Naming convention might differ based on the team. But one which you would see commonly is:

`feature/<jira-ticket-id>-short-title`

Common prefixes (sometimes same as the commit prefixes):
1. feature or feat
2. docs
3. hotfix
4. fix
5. release

Again, it depends on the team. Some teams have ci/cd setup that would work differently based on  the branch names, so be careful and consult your team mates before doing anything.

It is important to note that there are certain reserved keywords that Git uses like HEAD (which is used to depict the latest commit that we are working on) which are not to be used. [[1]]({{< relref "#references" >}})

## 3. Pull / Merge Request (PR/MR)

### PR/MR Title and Description

#### Title

The Title just like many other entities depends on your team. Consult teammates for the appropriate PR/MR Titles.

Commonly used title:

`<prefix>(brief-title): Title of the PR <JIRA-ID/tracking-id>`

eg: *feat(registration-api): adds POST API for registering Tenant TEN-1234*

#### Description

A PR/MR description should have a all the relevant information for someone to understand the changes that have been done. It should include the following sections:
1. What changes have been done?
1. Why those changes were done? Is is a new feature (explain it), a bug fix (add tracking ID) or periodic refactoring activity?
1. Additional resources that were created? Eg: AWS S3 resource might be created and added in IaC code repo. Add these additional PRs/MRs that goes with this change.
1. Testing scenarios, including the small description about dev level testing that was performed. This would help the reviewer verify the logic.
1. Miscellaneous information that the Reviewer should be aware of. Eg: The changes in postman collections, relevant documentation etc

### Before giving it off for review

Probably the most important take away: Make sure your PR/MR is ready before you send it off to review (by adding the reviewers).

Please be mindful of your teammates' time. It is annoying, to get the PR/MR and Unit tests are not complete or the test stage in the CI/CD pipeline is breaking. Ideally, have a PR/MR templates defined. [[3]]({{< relref "#references" >}}) [[4]]({{< relref "#references" >}})

Some of the checklist items worth considering:
1. **Rebase with the Default Branch**: Make sure you rebase your branch before you give it off to review. Resolve merge conflicts (if any).
2. **CI/CD Pipeline**: Please don't share your PR/MR if the CI/CD stages have not successfully executed yet. Make sure these execute completely before sending it off for review. As a reviewer, it is extremely frustrating to review the changes and only to know that some check failed and the assignee needs to rework and so does the reviewer.
3. **Testing**: When you share your PR, it mean the code works and it will work when merged. So Integration, Smoke testing is must before sending it off for review. Unit tests, being at the bottom of the testing pyramid, needs to be through. Please don't try to do this step parallelly unless you are really short in time. Test throughly and preferrably share the testing scenarios in the comments in PR/MR along with any associated documentation.
4. **Self-review**: If you made it so far after raising a PR, congratulations. But you can still make it easier for yourself and your reviewer. SELF REVIEW. Avoid skipping this step. I have personally found that many of the basic issues that my reviewers found, early in my careers, were the ones I could have resolved beforehand if I reviewed my code. This could have prevented multiple rounds of review and unnecessary embarrassment of making silly mistakes.
5. **Open-mindedness**: Early in the career, you make mistakes, and its okay.  It important to learn from those mistakes. This learning takes a backseat, the moment the code is tied to the ego. Even for seasoned developers, having an open mind to consider the alternate approach is essential. This would help you grow. Often times, you are surrounded by people with diverse experience, which is a great learning resource. It is easier said than done, but worth a try.



## References { #references }
[1] https://graphite.dev/guides/git-branch-naming-conventions#git-branch-name-restrictions

[2] https://cbea.ms/git-commit/

[3] https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/creating-a-pull-request-template-for-your-repository

[4] https://docs.gitlab.com/ee/user/project/description_templates.html#create-a-merge-request-template

[5] https://dev.to/puritanic/how-are-you-writing-a-commit-message-1ih7

[6] https://gist.github.com/joshbuchea/6f47e86d2510bce28f8e7f42ae84c716

[7] https://kapeli.com/cheat_sheets/Conventional_Commits.docset/Contents/Resources/Documents/index
