# 🛠️ Git Workflow & Troubleshooting Case Study
**Project:** Publishing a Local Infrastructure Project to GitHub  
**Engineer:** Frank Fru
[Architecture Diagram](architecture-diagram.png)
---

## 1. Overview & Challenge 🚩
**Goal:** Successfully publish a multi-file local Terraform project (`secure-url-shortener-tf`) to a remote GitHub repository.

**The Challenge:** The deployment was obstructed by interlocking system and synchronization errors including repository 404s, branch mismatches, and local system lock-file conflicts (`.git/index.lock`). This study documents the systematic approach taken to resolve these issues.

---

## 2. The Diagnostic Matrix 🔍
I encountered three simultaneous critical errors. Here is the engineering resolution path:

| Error Message | Root Cause | Engineering Resolution |
| :--- | :--- | :--- |
| `fatal: repository not found` | Remote URL was set locally, but repo didn't exist on server. | Created the empty repository via GitHub UI. |
| `fatal: index.lock: File exists` | A crashed Git process left a blocking lock file. | Executed `rm -f .git/index.lock` to unblock system. |
| `error: src refspec main does not match` | Local branch had no commits saved to push. | Initialized with `git add .` and `git commit`. |

---

## 3. Successful Outcome ✅
The final verification using `git push` and `git status` confirmed total synchronization:
> *On branch main. Your branch is up to date with 'origin/main'. nothing to commit, working tree clean.*

---

## 4. Live Links & Resources
* **Live Infrastructure Code:** [Secure URL Shortener (Terraform)](https://github.com/chifru19/secure-url-shortener-tf)
* **Tools Used:** VS Code, Git CLI, GitHub.
