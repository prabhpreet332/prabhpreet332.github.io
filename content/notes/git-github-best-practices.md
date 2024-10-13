+++
title = '[Draft] Version Control Best Practices'
date = 2024-10-12T00:45:42+05:30
description = "Best practices around using the version control softwares like git"
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

There Are some generic suggestion that would improve the workflow drastically

1. make sure to use the vendor specific features like Labels & Project (GH) and Milestones (GL) Use Case:
    1. One of the places I am getting to use GitHub Labels is to have the End-of-Quarter or End-of-Month deployments tracking of PRs / Issues.
    2. Labels also come in handy when you need to filter the PRs that are under review and the ones that needs to be merged.
    3. Another use case is when we need to group the PRs based on functionality we are implementing which is distributed amongst different developers and need to be merged all to get the feature to work in your internal environment.



## 1. Writing Commits
### Generic suggestion
1. **Keep you commit size small.**

The whole point of having the commits (ie snapshots of your code) is so that you can reference it and revert (if needed) in later point of time. But if you have a commit that has changes in 10 files or a logically complex change, then what's the point.

2. **Avoid amending comments.**

Amending comments to correct the title, description, or the file changes, is not usually a good idea.


### Commit Title and description

1. **Have the commit message in Imperative (commanding) tone.**

Reason: **Git itself uses the imperative whenever it creates a commit on your behalf.** [2]

Eg:
i. *Add input validation for registration API*
ii. *Bump minor version from v1.2.3 to 1.3.0*

https://dev.to/jacobherrington/how-to-write-useful-commit-messages-my-commit-message-template-20n9

https://www.freecodecamp.org/news/how-to-write-better-git-commit-messages/

2.


### Commit Signing

Always sign the commits. Follow the guide by [GitHub - Commit Signing](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits) and [FreeCodeCamp - What is commit signing in Git?](https://www.freecodecamp.org/news/what-is-commit-signing-in-git/).

## 2. Branches
Nameing convention might differ based on the team. But one which you would see commonly is:

`feature/<jira-ticket-id>-short-title`

prefix:
1. feature or feat
2. docs
3. hotfix
4. fix
5. release

again depends on the team. Some teams have ci/cd setup that would work differently based on  the branch names, so be careful and consult your team mates before doing anything.

It is important to note that there are certain reserved keywords that Git uses like HEAD (which is used to depict the latest commit that we are working on). [[1]]({{< relref "#references" >}})

## 3. Pull / Merge Request (PR/MR)

### PR/MR Title and Description

The Title just like many other entities depends on your team. Consult teammates for the appropriate PR/MR Titles.

`<specifier>(brief-title): Title of the PR <JIRA-ID or some tracking-id>`

eg: *feat(registration-api): adds POST API for registering Tenant TEN-1234*

### Before giving it off for review
rebase with the default branch

CI/CD checks clears

test - ut, e2e

self review

have open mind about the reviews

## Further Links

## References { #references }
[1] https://graphite.dev/guides/git-branch-naming-conventions#git-branch-name-restrictions

[2] https://cbea.ms/git-commit/
