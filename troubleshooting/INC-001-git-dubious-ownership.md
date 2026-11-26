# INC-001 - Git Dubious Ownership



## Incident Information

- **Date:** November 25, 2026
- **Category:** Git Configuration

- **Priority:** Low
- **Status:** Resolved

## Environment

- **Operating System:** Windows 11 Home
- **Git Version:** git version 2.56.0.windows.2
- **Terminal:** Git bash UCRT64

## Problem Description

I was unable to run git remote -v or git status in Git Bash

## Error Message
```
fatal: detected dubious ownership in repository at 'H:/IT-Projects/enterprise-it-homelab'

'H:/IT-Projects/enterprise-it-homelab' is on a file system that does not record ownership

To add an exception for this directory, call:


git config --global --add safe.directory H:/IT-Projects/enterprise-it-homelab
```

## Troubleshooting steps

1. Ran git config --get-all safe.directory to verify H:/IT-Projects/enterprise-it-homelab was not listed as a safe.directory

## Root Cause

H:/IT-Projects/enterprise-it-homelab was not recognized as a safe.directory because I had not explicitly told Git I am the owner and trust this repository

## Resolution

Ran the call command git config --global --add safe.directory H:/IT-Projects/enterprise-it-homelab to have Git recognize it as a safe directory.

## Verification

Reran git status and git remote -v for verification that they work and the safe.directory was updated
```

$ git status

On branch main

Your branch is up to date with 'origin/main'.



nothing to commit, working tree clean
```

```

$ git remote -v

origin  https://github.com/PenguIsland/enterprise-it-homelab (fetch)

origin  https://github.com/PenguIsland/enterprise-it-homelab (push)
```



## Lesson Learned

When making certain edits to repositories ensure safety ownership as a safe.directory. This tells git that I as the user trust the repository and to allow access for certain verification commands to run 


