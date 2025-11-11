

---



### **1. Git Rebase**

- **Definition:**  
    `git rebase` re-applies commits from one base to another, producing a **linear history**.  
    It’s useful to **keep feature branches up to date** with the main branch.
    
- **Key Points:**
    
    - It **rewrites commits**, which changes their history.
        
    - **Do NOT rebase commits** that are already pushed to a shared branch unless **all collaborators coordinate**.
        
    - If rebase produces conflicts, **resolve them** and continue with:
        
        ```bash
        git rebase --continue
        ```
        
    - It allows performing actions without creating unnecessary commits.
        

---

### **2. Git Revert**

- **Definition:**  
    `git revert` creates a **new commit** that **undoes** the changes introduced by a previous commit.  
    This makes it **safe for public or shared branches** because it **preserves history**.
    
- **Key Points:**
    
    - Commonly used in **public repositories**.
        
    - Unlike `git reset`, it does **not delete commit history**.
        
    - Example usage:
        
        ```bash
        git revert <commit-hash>
        ```
        
    - **Comparison:**
        
        - `git revert` → Safe for public/shared branches.
            
        - `git reset` → Used for private branches or local cleanup.
            

---

### **3. Git Stash**

- **Definition:**  
    `git stash` temporarily saves your **uncommitted changes** (both working directory and index) to a **stack-like storage**, allowing you to switch branches or perform other tasks cleanly.
    
- **Key Points:**
    
    - Helps when you need to **pause work** without committing incomplete changes.
        
    - Stashes are **local** and **not shared** unless you explicitly create a branch and commit them.
        
    - Use cases:
        
        - **Save current progress:**
            
            ```bash
            git stash
            ```
            
        - **List stashes:**
            
            ```bash
            git stash list
            ```
            
        - **Apply latest stash:**
            
            ```bash
            git stash apply
            ```
            
        - **Discard stash:**
            
            ```bash
            git stash drop
            ```
            

---

### **4. Git Cherry-Pick**

- **Definition:**  
    `git cherry-pick` applies a specific commit from **another branch** onto your **current branch**, creating a **new commit with the same changes**.
    
- **Example Usage:**
    
    ```bash
    git cherry-pick <commit-hash>
    ```
    
- **Use Case:**  
    Useful for selectively adding fixes or features from one branch to another without merging the entire branch.
    

---

### **5. Git Reset**

- **Definition:**  
    `git reset` moves the **HEAD** pointer and optionally modifies the staging area and working directory to match a specified commit.
    
- **Types of Reset:**
    
    - **Soft Reset:** Keeps changes staged
        
        ```bash
        git reset --soft <commit-hash>
        ```
        
    - **Mixed Reset (default):** Keeps changes in working directory but unstaged
        
        ```bash
        git reset <commit-hash>
        ```
        
    - **Hard Reset:** Deletes all changes permanently
        
        ```bash
        git reset --hard <commit-hash>
        ```
        
- **Use Case:**  
    Ideal for **private branches** when cleaning up or editing commit history before pushing.
    

---

### **6. Tagging Commits**

- **Purpose:**  
    Tags are used to **mark specific points** in a repository’s history (e.g., releases or versions).
    
- **Types of Tags:**
    
    - **Lightweight Tag:** A simple name pointer to a commit.
        
        ```bash
        git tag v1.0
        ```
        
    - **Annotated Tag:** Stores metadata such as tagger name, date, and message.
        
        ```bash
        git tag -a v1.0 -m "Version 1.0 release"
        ```
        
- **Push Tags to Remote:**
    
    ```bash
    git push origin <tagname>
    ```
    
    or all tags:
    
    ```bash
    git push origin --tags
    ```
    

---

