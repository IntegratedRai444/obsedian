 **Unnormalized Form → 1NF → 2NF → 3NF → BCNF → 4NF**, along with **functional dependencies**, **trivial**, **non-trivial**, **semi non-trivial**, and **transitive dependency**.

---

## 📘 **Normalization in DBMS (Arc of DBMS)**

### 🔹 **Definition**

**Normalization** is the process of organizing data in a database to **eliminate redundancy** and **ensure data integrity**.  
It divides larger tables into smaller, related tables and defines relationships between them.

---

## 🧩 **Functional Dependency (FD)**

When **one attribute determines another**, it’s called a **Functional Dependency**.

> **Notation:**  
> A → B  
> means **Attribute A functionally determines B**

**Example:**

|Roll_No|Name|Department|
|---|---|---|
|101|Raj|CSE|

Here, **Roll_No → Name, Department**  
(because Roll_No uniquely identifies the student)

---

## ⚙️ **Types of Functional Dependencies**

|Type|Definition|Example|
|---|---|---|
|**Trivial FD**|When the dependent attribute is a subset of determinant.|A → A or AB → A|
|**Non-Trivial FD**|When the dependent is not a subset of determinant.|Roll_No → Name|
|**Semi Non-Trivial FD**|When some part of dependent attribute is also in determinant.|AB → B, C (B is in determinant, C is not)|

---

## 🔄 **Transitive Dependency**

A **transitive dependency** occurs when:

> A → B and B → C ⇒ A → C

It means an attribute depends **indirectly** on a primary key through another attribute.

**Example:**

|Roll_No|Dept_ID|Dept_Name|
|---|---|---|
|101|D1|CSE|

Here:

- Roll_No → Dept_ID
    
- Dept_ID → Dept_Name  
    ⇒ Roll_No → Dept_Name (transitive dependency)
    

**In 3NF**, we **remove transitive dependencies**.

---

## 🧱 **Normal Forms Explained**

|Normal Form|Rule|Focus|
|---|---|---|
|**1NF (First Normal Form)**|No repeating groups or multivalued attributes. Each cell must hold **atomic** values.|Remove **multivalued attributes**.|
|**2NF (Second Normal Form)**|Must be in 1NF and all **non-key attributes** must depend on the **whole primary key** (no partial dependency).|Remove **partial dependency**.|
|**3NF (Third Normal Form)**|Must be in 2NF and **no transitive dependency** exists.|Remove **transitive dependency**.|
|**BCNF (Boyce–Codd Normal Form)**|For every FD A → B, **A must be a super key**.|Remove **anomalies** caused by overlapping candidate keys.|
|**4NF (Fourth Normal Form)**|Must be in BCNF and have **no multivalued dependencies**.|Remove **multivalued dependency**.|

---

## 🧮 **Example Normalization Step-by-Step**

### **Unnormalized Table**

|Student_ID|S_Name|Course|S_Phone|S_Address|DOB|
|---|---|---|---|---|---|
|GF202455815|Rishabh Kapoor|{CSE-AI/ML, AI/DS}|{8988344500, 9876543210}|{Mandi, H.P; Chandigarh}|30/05/2007|
|GF202456844|Aayush|{CSE-AI/ML, CSE-Core}|{9234502934, 9012345678}|{Bihar, Patna}|21/05/2004|
|GF202453455|Aryan|{AI/DS, CSE-AI/ML}|{9234523455, 9123456789}|{Dharamshala, Kangra}|11/07/2006|

---

 ✅ **1st Normal Form (1NF)**

- Remove multivalued attributes — every cell should have a single atomic value.
    

|Student_ID|S_Name|Course|S_Phone|S_Address|DOB|
|---|---|---|---|---|---|
|GF202455815|Rishabh Kapoor|CSE-AI/ML|8988344500|Mandi, H.P|30/05/2007|
|GF202455815|Rishabh Kapoor|AI/DS|9876543210|Chandigarh|30/05/2007|
|GF202456844|Aayush|CSE-AI/ML|9234502934|Bihar|21/05/2004|
|GF202456844|Aayush|CSE-Core|9012345678|Patna|21/05/2004|
|GF202453455|Aryan|AI/DS|9234523455|Dharamshala|11/07/2006|
|GF202453455|Aryan|CSE-AI/ML|9123456789|Kangra|11/07/2006|

---

### ✅ **2nd Normal Form (2NF)**

- Table must be in 1NF.
    
- Remove **partial dependency** (attributes that depend on part of composite key).
    

Split into two tables:

#### 🧩 Table 1: Student Details

|Student_ID|S_Name|DOB|
|---|---|---|
|GF202455815|Rishabh Kapoor|30/05/2007|
|GF202456844|Aayush|21/05/2004|
|GF202453455|Aryan|11/07/2006|

#### 🧩 Table 2: Student_Courses

|Student_ID|Course|
|---|---|
|GF202455815|CSE-AI/ML|
|GF202455815|AI/DS|
|GF202456844|CSE-AI/ML|
|GF202456844|CSE-Core|
|GF202453455|AI/DS|
|GF202453455|CSE-AI/ML|

#### 🧩 Table 3: Student_Contacts

|Student_ID|S_Phone|S_Address|
|---|---|---|
|GF202455815|8988344500|Mandi, H.P|
|GF202455815|9876543210|Chandigarh|
|GF202456844|9234502934|Bihar|
|GF202456844|9012345678|Patna|
|GF202453455|9234523455|Dharamshala|
|GF202453455|9123456789|Kangra|

---

### ✅ **3rd Normal Form (3NF)**

- Remove **transitive dependencies**.  
    If Address → City or State, then separate Address details.
    

#### 🧩 Table 4: Address_Info

|Address_ID|City|State|
|---|---|---|
|1|Mandi|H.P|
|2|Chandigarh|U.T.|
|3|Bihar|Bihar|
|4|Patna|Bihar|
|5|Dharamshala|H.P.|
|6|Kangra|H.P.|

Then in Student_Contacts:

|Student_ID|S_Phone|Address_ID|
|---|---|---|
|GF202455815|8988344500|1|
|GF202455815|9876543210|2|
|GF202456844|9234502934|3|
|GF202456844|9012345678|4|
|GF202453455|9234523455|5|
|GF202453455|9123456789|6|

---

### ✅ **BCNF (Boyce–Codd Normal Form)**

- Each **determinant must be a superkey**.
    
- Our structure now satisfies this — all FDs have keys determining non-key attributes.
    

---

### ✅ **4th Normal Form (4NF)**

- Remove **multivalued dependencies** (attributes that are independent but both depend on the same key).
    

Here:

- Student_ID → Course
    
- Student_ID → S_Phone  
    are independent MVDs, so we separate them (already done in 2NF).
    

So final structure **satisfies 4NF**.

---

## 🧠 **Summary Table**

|Normal Form|Removes|Key Concept|
|---|---|---|
|**1NF**|Repeating groups|Atomic values only|
|**2NF**|Partial dependency|Each non-key attribute depends on whole key|
|**3NF**|Transitive dependency|Non-key attributes depend only on key|
|**BCNF**|Anomalies from overlapping candidate keys|Each determinant is a superkey|
|**4NF**|Multivalued dependency|Independent multi-valued facts separated|

---

Would you like me to make this into a **color-coded PDF cheat sheet** (for printing or notes)?  
It can include a clear diagram of dependencies and the normalization flow (Unnormalized → 4NF).