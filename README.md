# 📚 Smart Cloud-Based Book Tracking System

### ✨ INT 330 – Managing Cloud Solutions | CA 2 Project

**Project Title:** *Helping Readers Stay on Track with Their Reading Goals*

---

## 🔍 Project Overview

Many readers struggle with tracking their reading progress due to busy schedules or forgetting to log sessions. This leads to unfinished books, loss of motivation, and no insights into their habits.

This project introduces a **cloud-hosted, intelligent reading assistant** that:

* Logs books and reading time
* Predicts when you'll finish based on pace
* Sends reminders if you stop reading
* Generates monthly progress reports
* Runs seamlessly on AWS cloud infrastructure

---

## 🧩 Features

* 📖 Log books (title, author, start/end date, page count)
* ⏱ Track and update reading time per session
* 📈 Predict completion date using current pace
* 🔔 Auto-reminders via email using AWS SNS
* 📊 Monthly reading summary reports
* ☁️ Runs entirely on AWS with automation and monitoring

---

## 🛠 AWS Architecture

| Component               | Description                           |
| ----------------------- | ------------------------------------- |
| **Amazon EC2**          | Hosts Flask web app with Bootstrap UI |
| **Amazon RDS (MySQL)**  | Stores book logs, reading sessions    |
| **AWS Lambda**          | Triggers reading reminders            |
| **Amazon SNS**          | Sends reminder emails to readers      |
| **Amazon CloudWatch**   | Triggers Lambda daily, monitors logs  |
| **VPC Security Groups** | Secures access to EC2/RDS (HTTP, SSH) |
| **MySQL Workbench**     | Manages database schema and data      |

---

## 🧱 System Workflow

1. **User logs a book** → Stored in **RDS MySQL**
2. **User starts a session** → Time tracked and updated
3. **No reading activity?** → **CloudWatch** triggers **Lambda**
4. **Lambda** checks for inactivity → Sends **SNS Email Reminder**
5. **Reports** generated using query aggregation for summaries

---

## ⚙️ Setup & Deployment Instructions

### 1. **Launch EC2 & Setup Flask App**

* Ubuntu AMI + Python 3.10
* Install Flask, MySQL connector, Bootstrap for UI
* Upload and run Flask app (`python app.py`)

### 2. **Configure RDS (MySQL)**

* Launch RDS (MySQL) in same VPC
* Create `books` and `reading_sessions` tables
  

### 3. **Connect Flask to RDS**

* Use `mysql-connector-python`
* Store DB config securely using environment variables

### 4. **Set up Lambda + SNS + CloudWatch**

* Create SNS Topic → Add verified email subscribers
* Lambda Function (Python) checks inactivity → Triggers SNS
* CloudWatch Event Rule runs Lambda daily

### 5. **Security Configuration**

* EC2 Security Group: Allow `HTTP (80)` and `SSH (22)` from your IP
* RDS Security Group: Allow access from EC2 instance only

---

## 📬 Reminder Logic

* Check `reading_sessions` for last session per book
* If no entry in last 3 days → Trigger email reminder via SNS

---


## 📊 Monthly Report (Planned)

* Aggregated data on time spent, pages read
* Insights on pace and discipline
* Visual charts using Python + Matplotlib or JS chart libraries

---


## 🧑‍💻 Authors

**Shiwani Yaduka**
*Cloud Management Solutions*

---

## 📎 References

* [AWS EC2 Documentation](https://docs.aws.amazon.com/ec2/)
* [AWS RDS MySQL](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/CHAP_MySQL.html)
* [AWS SNS Setup](https://docs.aws.amazon.com/sns/)
* [Flask Documentation](https://flask.palletsprojects.com/)
* [MySQL Workbench](https://dev.mysql.com/downloads/workbench/)


