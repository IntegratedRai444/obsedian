

---

## **Version Control System (VCS)**

A **Version Control System (VCS)** not only allows us to save snapshots of a project but also provides mechanisms to **track, analyze, and modify** the project’s history.  
**Git**, being a **Distributed Version Control System (DVCS)**, offers powerful features to examine project evolution, mark important milestones, and, when necessary, **rewrite history**.

Every **commit** in Git acts as a **checkpoint** in the development timeline. It records:

- A unique identifier represented by a **hash (#)**
    
- **Author details**
    
- **Timestamp**
    
- A **descriptive message**
    
- A **snapshot** of project changes
    

---

## **Important Git Commands**

### **1. `git log`**

- Displays a chronological history of the project.
    
- Developers use logs to trace when bugs were introduced, understand design decisions, or review contributions.
    
- Visual variations such as graphical or condensed logs make it easier to see the branching structure and merges.
    

### **2. `git show`**

- Focuses on a single commit.
    
- Displays details such as:
    
    - Files modified
        
    - Specific lines edited or removed
        
    - Commit metadata
        

---

## **Tagging Commits**

**Tags** in Git are markers that highlight important points in the project’s history.  
They serve as simple references to any commit, including its hash and author details.

### **Annotated Tags**

Annotated tags carry additional information such as messages, version notes, and even security certificates.

**Why use tags?**

- To keep a record of various versions and follow release cycles.
    
- By tagging a commit, teams can always reproduce a stable version independent of ongoing development.
    

---

## **Changing Commit History**

Sometimes, wrong files get committed, bugs are introduced, or commit messages are unclear.  
To fix these issues, Git provides ways to **change or rewrite commit history**.

### **1. Rewrite Local History**

Commands:

- `git reset`
    
- `git rebase`
    
- `git commit --amend`
    

> ⚠️ These commands can **change the commit topology** and should be used carefully, especially for commits already pushed and shared.

---

### **2. Rewrite Public History**

- `git revert` is the **safe command** to undo changes in a **shared repository**.
    
- It creates a new commit that reverses the effects of an earlier one while **preserving the project’s history**.
    

---

## **`git reset` Overview**

The `git reset` command moves the current branch reference (**HEAD**) to a specified target commit, controlling both the **staging area** and **working directory**.

|Mode|HEAD Moves|Index Updated|Working Tree Updated|Typical Use|
|---|---|---|---|---|
|**soft**|Yes|No|No|Undo the last commit (keep changes staged).|
|**mixed**|Yes|Yes|No|Unstage files but keep changes in the working directory. _(default mode)_|
|**hard**|Yes|Yes|Yes|Discard commits and all working changes — **destructive**, not recommended.|

---

