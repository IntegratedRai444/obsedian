
---

## 📘 **Normalization in DBMS (Simplified Notes)**

### 🔹 What is Normalization?

**Normalization** is a process in DBMS used to:

- Organize data properly,
    
- Remove redundancy (repeated data),
    
- And make sure data is consistent and reliable.
    

It breaks a big complex table into smaller related tables.

---

## ⚙️ **Functional Dependency (FD)**

When **one attribute uniquely determines another attribute**, it is called a **Functional Dependency**.

👉 **Example:**

|Roll_No|Name|Department|
|---|---|---|
|101|Raj|CSE|

Here:  
**Roll_No → Name, Department**  
Because roll number uniquely identifies the name and department.

---

## 🔸 **Types of Functional Dependencies**

|Type|Meaning|Example|
|---|---|---|
|**Trivial Dependency**|When both sides have same attributes.|A → A or AB → A|
|**Non-Trivial Dependency**|When right side is not a part of the left side.|Roll_No → Name|
|**Semi Non-Trivial Dependency**|When some part of the right side is already in the left side.|AB → B, C|

---

## 🔹 **Transitive Dependency**

If **A → B** and **B → C**,  
then **A → C** (indirect dependency).

👉 **Example:**

|Roll_No|Dept_ID|Dept_Name|
|---|---|---|
|101|D1|CSE|

Here:  
Roll_No → Dept_ID and Dept_ID → Dept_Name  
so, Roll_No → Dept_Name (this is a **transitive dependency**)

---

## 🧠 **Why Normalization is Needed**

- To **remove duplicate data**
    
- To **avoid update, insert, and delete anomalies**
    
- To **make the database more efficient**
    

---

## 🧱 **Types of Normal Forms (Simplified)**

|Normal Form|Rule|What It Removes|
|---|---|---|
|**1NF (First Normal Form)**|Each column should have only **atomic (single)** values.|Removes **repeating or multivalued data**.|
|**2NF (Second Normal Form)**|Table should be in 1NF and **no partial dependency** on part of a composite key.|Removes **partial dependency**.|
|**3NF (Third Normal Form)**|Table should be in 2NF and **no transitive dependency**.|Removes **transitive dependency**.|
|**BCNF (Boyce–Codd Normal Form)**|For every dependency A → B, **A must be a super key**.|Removes **overlapping candidate key anomalies**.|
|**4NF (Fourth Normal Form)**|Table should be in BCNF and **no multivalued dependency**.|Removes **multivalued dependency**.|

---

## 🧩 **Example Step-by-Step Normalization**

### 🔴 **Unnormalized Table (UNF)**

|Student_ID|S_Name|Course|S_Phone|S_Address|DOB|
|---|---|---|---|---|---|
|GF202455815|Rishabh Kapoor|{CSE-AI/ML, AI/DS}|{8988344500, 9876543210}|{Mandi, H.P; Chandigarh}|30/05/2007|
|GF202456844|Aayush|{CSE-AI/ML, CSE-Core}|{9234502934, 9012345678}|{Bihar, Patna}|21/05/2004|
|GF202453455|Aryan|{AI/DS, CSE-AI/ML}|{9234523455, 9123456789}|{Dharamshala, Kangra}|11/07/2006|

**Problems:**

- Contains repeating (multivalued) data → Courses, Phone, and Address.
    

---

### 🟢 **1st Normal Form (1NF)**

➡️ Remove multivalued attributes — every column must have a single value.

|Student_ID|S_Name|Course|S_Phone|S_Address|DOB|
|---|---|---|---|---|---|
|GF202455815|Rishabh Kapoor|CSE-AI/ML|8988344500|Mandi, H.P|30/05/2007|
|GF202455815|Rishabh Kapoor|AI/DS|9876543210|Chandigarh|30/05/2007|
|GF202456844|Aayush|CSE-AI/ML|9234502934|Bihar|21/05/2004|
|GF202456844|Aayush|CSE-Core|9012345678|Patna|21/05/2004|
|GF202453455|Aryan|AI/DS|9234523455|Dharamshala|11/07/2006|
|GF202453455|Aryan|CSE-AI/ML|9123456789|Kangra|11/07/2006|

✅ Data is now **atomic** (single values only).

---

### 🟡 **2nd Normal Form (2NF)**

➡️ Remove **partial dependency** (when a column depends on part of a composite key).

We split the data into multiple tables.

#### (a) Student Table

|Student_ID|S_Name|DOB|
|---|---|---|
|GF202455815|Rishabh Kapoor|30/05/2007|
|GF202456844|Aayush|21/05/2004|
|GF202453455|Aryan|11/07/2006|

#### (b) Course Table

|Student_ID|Course|
|---|---|
|GF202455815|CSE-AI/ML|
|GF202455815|AI/DS|
|GF202456844|CSE-AI/ML|
|GF202456844|CSE-Core|
|GF202453455|AI/DS|
|GF202453455|CSE-AI/ML|

#### (c) Contact Table

|Student_ID|S_Phone|S_Address|
|---|---|---|
|GF202455815|8988344500|Mandi, H.P|
|GF202455815|9876543210|Chandigarh|
|GF202456844|9234502934|Bihar|
|GF202456844|9012345678|Patna|
|GF202453455|9234523455|Dharamshala|
|GF202453455|9123456789|Kangra|

✅ Now, all non-key attributes depend fully on the primary key.

---

### 🔵 **3rd Normal Form (3NF)**

➡️ Remove **transitive dependency** (indirect dependency).

If Address determines City or State, make a separate table for Address details.

#### Address Table

|Address_ID|City|State|
|---|---|---|
|1|Mandi|H.P|
|2|Chandigarh|U.T.|
|3|Bihar|Bihar|
|4|Patna|Bihar|
|5|Dharamshala|H.P.|
|6|Kangra|H.P.|

Then update Contact Table:

|Student_ID|S_Phone|Address_ID|
|---|---|---|
|GF202455815|8988344500|1|
|GF202455815|9876543210|2|
|GF202456844|9234502934|3|
|GF202456844|9012345678|4|
|GF202453455|9234523455|5|
|GF202453455|9123456789|6|

✅ No transitive dependency now.

---

### 🟣 **BCNF (Boyce–Codd Normal Form)**

➡️ For every dependency **A → B**, A must be a **super key**.  
Our design already follows this, so ✅ it is in BCNF.

---

### ⚪ **4th Normal Form (4NF)**

➡️ Remove **multi-valued dependencies** — if one key determines two independent multi-valued attributes, split them.

Here,

- Student_ID → Course
    
- Student_ID → S_Phone
    

Both are independent, and we already separated them into different tables.  
✅ So, this is in **4NF**.

---

## ✅ **Summary Table**

|Normal Form|What It Fixes|Rule|
|---|---|---|
|**1NF**|Repeating or multivalued columns|Keep single (atomic) values only|
|**2NF**|Partial dependency|Every non-key depends on full key|
|**3NF**|Transitive dependency|Non-key attributes depend only on key|
|**BCNF**|Key anomalies|Each determinant is a super key|
|**4NF**|Multivalued dependency|Separate independent multivalued data|

---
