# 📊 Monthly Assessment Marks Calculation – n8n Workflow

This repository contains an automated workflow built in **n8n** for calculating monthly assessment marks for two course tracks:  
**DA (Data Analytics)** and **DS (Data Science)**.

The workflow collects student details, prompts for module-wise marks, computes average scores using Python code, and then determines **eligibility** based on a predefined threshold.

---

## 🎯 Objective
It aims to automate the process of calculating monthly assessment marks for all students.
The goal is to automatically compute each student’s average score and determine whether they are eligible for the placement drive.
You are required to design and implement this automation workflow using n8n.

---

## 🧠 Scenario
Innomatics wants to simplify the monthly assessment evaluation by:
- Collecting module-wise marks via N8n Form.
- Automatically calculating the average marks.
- 
Providing a status message based on performance:
- ✅ Eligible if average marks > 70.
- ⚠️ Not Eligible if average marks ≤ 70, with suggestions on which modules need improvement.

---

## 🚀 Features

- 📥 **Form-based data collection** for student name & course  
- 🔀 **Branching logic** to route users to DA or DS mark entry forms  
- 🧮 **Automatic calculation of average marks** using Python  
- ✔️ **Eligibility check** using conditional logic  
- 🎉 **Dynamic personalized output** showing Eligible / Not Eligible result  
- 🔗 Fully built with **n8n no-code workflow automation**

---

## 🧩 Workflow Structure

Below is the step-by-step flow implemented inside the n8n project:

### 1. **On Form Submission**
The workflow begins by collecting:
- Student Name  
- Course (DA / DS)

The subsequent flow is determined by the course selection.

---

### 2. **Switch Node – Course Routing**
This node directs the user to the appropriate mark-entry form:

| Course | Redirects To |
|--------|--------------|
| DA     | Enter DA Marks |
| DS     | Enter DS Marks |

---

### 3. **Enter DA Marks Form**
The DA student enters marks for 5 modules:
- Python  
- EDA  
- SQL  
- Power BI  
- Adv_Stats  

---

### 4. **Enter DS Marks Form**
The DS student enters marks for:
- ML  
- ANN  
- CNN  
- NLP  
- GenAI  

---

### 5. **Average Marks Calculation**

#### DA Calculation Code
\`\`\`
return [{
    "Total Average Marks": (
        _items[0]["json"]["Python"] +
        _items[0]["json"]["EDA"] +
        _items[0]["json"]["SQL"] +
        _items[0]["json"]['Power BI'] +
        _items[0]["json"]["Adv_Stats"]
    ) / 5
}];\`\`\`

#### DS Calculation Code
```python
return [{
    "Total Average Marks": (
        _items[0]["json"]["ML"] +
        _items[0]["json"]["ANN"] +
        _items[0]["json"]["CNN"] +
        _items[0]["json"]["NLP"] +
        _items[0]["json"]["GenAI"]
    ) / 5
}];```

