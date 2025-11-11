

## **Git – Distributed Version Control System (DVCS)**

Git is a **distributed version control system** used to **track changes** in software development. It allows **multiple developers to collaborate** on the same project **simultaneously** without interfering with each other’s work.

### **Key Features of Git**

1. **Distributed** – Every developer has a **full copy of the repository**, including the entire history.
    
    - **Benefit:** Fast and lightweight operations.
        
2. **Git Operations** – Most operations like commits and branching are **local and quick**.
    
    - **Benefit:** No need for constant internet or server access.
        
3. **Tracks History** – Git records changes over time and allows you to **rollback** to earlier versions.
    
4. **Supports Branching and Merging** – Developers can work on **multiple features or fixes in parallel** and merge changes later.
    

---

Version Control System (VCS)

A **VCS** is a system that **records changes to files over time**, allowing you to **recall specific versions** when needed.

### **Key Concepts of VCS**

|**Term**|**Description**|
|---|---|
|**Repositories**|Directory containing your project and Git tracking information.|
|**Commit**|A snapshot of your files at a specific point in time.|
|**Staging Area**|A space where changes are prepared before committing.|
|**Working Directory**|Your actual project files where you make edits.|
|**Branch**|A separate line of development for features or experiments.|
|**Merge**|Integrates changes from one branch into another.|
Version control helps in collaborative development, rollback after mistakes and understanding evolution 

-----------------------------------------------------------------------------

| features      | git                                         | github                                                         |
| ------------- | ------------------------------------------- | -------------------------------------------------------------- |
| Type          | VCS                                         | Web based hosting for github repo                              |
| Functions     | Tracks changes of source code locally       | Host git repo online for collaborations                        |
| Installation  | Installation needed locally CLI/GUI         | Not mendatory as no installation needed can be used in browser |
| usage         | manage version control locally              | share,review,collaborate ,                                     |
| autentication | no account needed                           | requires github account                                        |
| Access type   | command line/IDE integration                | web interface+gitCLI                                           |
| features      | branching,commiting,merging,staging,tagging | pull requests,issues, ci/cd                                    |
|               |                                             |                                                                |

## **Git Three-Tree Architecture**

Git uses a **three-tree architecture** that fundamentally differs from other version control systems.  
This architecture provides Git with its **power, flexibility, and safety features**.  
Mastering Git workflows and understanding this architecture can help you **avoid common pitfalls**.

**The Three Trees are:**

1. **Working Directory (Working Tree)**
    
2. **Staging Area (Index)**
    
3. **Repository (.git directory)**
    

---

### **1. Working Directory (Working Tree)**

The **working directory** represents your project’s current state — the files and directories you can see and edit in your file system.

**Characteristics:**

- **Visible Files** – Actual files you work on in a text editor or IDE.
    
- **Current State** – Represents the latest version you have checked out.
    
- **Editable** – You can create, modify, and delete files here.
    
- **Untracked Files** – New files that Git isn’t yet tracking.
    
- **Modified Files** – Files that have changed since the last commit.
    

**File States in the Working Directory:**

1. **Untracked** – Newly created files that Git doesn’t know about until they are staged.
    
2. **Modified** – Existing files that have been changed since the last commit.
    
3. **Deleted** – Files removed from the working directory.
    

---

### **2. Staging Area (Index)**

The **staging area** is an intermediate space between the working directory and the repository.  
It’s where you prepare and organize changes before committing them.

**Characteristics:**

1. **Preparation Area** – Holds a snapshot of what will be included in the next commit.
    
2. **Selective Staging** – You can choose which changes to commit.
    
3. **Snapshot Preview** – Lets you review the exact state of the next commit.
    
4. **Hidden from View** – Stored in `.git/index` and not directly visible in the file system.
    

**Purpose & Benefits:**

- **Granular Control** – Stage only specific changes instead of entire files.
    
- **Commit Preparation** – Review and organize changes before making them permanent.
    
- **Partial Commits** – Commit related changes separately for cleaner history.
    
- **Safety Net** – Prevents accidental commits by requiring explicit staging.
    

---

### **3. Repository (.git Directory)**

The **repository** is Git’s permanent storage. It contains all committed changes, history, branches, and metadata.

**Components of the Repository:**

- **Objects Database** – Stores Git objects such as commits, trees (directory structures), and blobs (file contents).
    
- **References** – Includes branch pointers, tags, and the `HEAD` pointer.
    
- **Hooks** – Custom scripts that run automatically at specific Git events.
    

**Types of Git Objects Stored:**

- **Trees** – Directory structures for project snapshots.
    
- **Commits** – Snapshots of the entire project with metadata (author, date, message).
    
- **Tags** – Named references to specific commits.



| working directory |     |     |
| ----------------- | --- | --- |
|                   |     |     |
|                   |     |     |
