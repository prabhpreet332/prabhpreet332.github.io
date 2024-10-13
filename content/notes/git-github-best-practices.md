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

disableHLJS = false # to disable highlightjs
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

## Why should you care?

In a single line: It will make the your and your teammates' life easier.


### Disclaimer

1. Many people have written on this topic. I would present my take based on the experiences I had so far. So by all means, this is not an exhaustive list. Feel free to have a discussion about this in the [issues]({{< param "GlobalValues.repository-management.blog-github-issues-url" >}}) / [discussions]({{< param "GlobalValues.repository-management.blog-github-discussions-url" >}}) sections.

2. I made many mistakes with these practices and am still learning.

3. This is aimed at the devs who are joining the workforce for the first time and for the seasoned devs who might like to have a refresher.

## Best Practices

## 1. Writing Commits
### Generic suggestion
1. Keep you commit size small.
The whole point of having the commits (ie snapshots of your code) is so that you can reference it and revert (if needed) in later point of time. But if you have a commit that has changes in 10 files or a logically complex change, then what's the point.

### Commit Title

### Commit Description

### Commit Signing

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

It is important to note that there are certain reserved keywords that Git uses like HEAD (which is used to depict the latest commit that we are working on). [1]

## 3. Pull / Merge Request (PR/MR)

### PR/MR Title

### PR/MR Description

### Before giving it off for review
rebase with the default branch

CI/CD checks clears

test - ut, e2e

self review

have open mind about the reviews

## Further Links

## References
[1] https://graphite.dev/guides/git-branch-naming-conventions#git-branch-name-restrictions
