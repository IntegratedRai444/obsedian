Version Control Systems (VCS) were first introduced to manage changes to files over time.

The initial systems were **local VCS**, which included tools like the **Revision Control System (RCS)**. These stored file versions on individual machines.  
**Drawback:** They did not support collaboration between multiple developers.

To overcome this, **Centralized VCS** was introduced. It included tools like **Microsoft Visual SourceSafe (VSS)**, based on a central server architecture. However, it had some limitations:

1. Required constant network access.
    
2. Merging changes was difficult.
    
3. Single point of failure (if the server went down, the whole system was affected).
    

In a centralized server architecture, a single server controls the entire system and stores the complete project data, which can then be accessed by multiple users.


Disturtive VCS 
It includes tools liek git and merc 
it includes full local repo ,offline support and safer branching and merging 



| features    | cvcs                            | dvcs                                             |     |
| ----------- | ------------------------------- | ------------------------------------------------ | --- |
| repo        | in this single central repo     | every developer has a full copy                  |     |
| network     | fully dependent for all actions | partially dependent except when sync is required |     |
| speed       | slower due to server dependency | fast as most actions are local                   |     |
| reailbility | poor                            | good as every developer has a backup             |     |
|             |                                 |                                                  |     |
