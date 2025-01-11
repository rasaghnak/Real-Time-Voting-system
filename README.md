# Realtime Election Voting System on AWS

Hi there! 👋

This is a project I’ve worked on to demonstrate my ability to design and implement a **Realtime Election Voting System** using **AWS services**. The idea behind this project was to build a scalable, reliable, and real-time system to process and analyze election voting data in real time. I wanted to showcase my skills in cloud-native development, data engineering, and building end-to-end solutions that solve real-world problems.

---

## 🎯 Project Highlights

Here’s what this project does:
- **Real-Time Vote Processing**: Processes voting events in real time using Kafka (Amazon MSK).
- **Enriches and Aggregates Data**: Combines voting data with additional details like candidate and voter information from a relational database (Amazon RDS).
- **Scalable Data Storage**: Stores all processed data securely in Amazon S3 for further analysis and querying.
- **Real-Time Analytics Dashboard**: Visualizes voting trends live using Amazon QuickSight.

I wanted this project to reflect what I would do in a real-world scenario, so I designed it to be **cloud-native**, scalable, and focused on actionable insights.

---

## 🏗 System Overview

Here’s a quick breakdown of how it works:

1. **Vote Submission**: Voters cast their votes, and the votes are sent to Kafka topics (via Amazon MSK).
2. **Data Enrichment**: A Lambda function processes these votes in real time, enriching them with details like voter region and candidate name (retrieved from RDS).
3. **Data Storage**: The enriched data is stored in Amazon S3 for both historical analysis and live querying.
4. **Analytics and Visualization**: Using Amazon Athena and QuickSight, I created real-time dashboards to showcase voting trends, candidate popularity, and regional breakdowns.

### System Architecture:

![System Architecture](system_architecture.jpg)

---

## 💼 Why This Project?

This project highlights my ability to:
- **Design Real-Time Systems**: Working with Amazon MSK (Kafka) for low-latency, high-throughput data streaming.
- **Build Scalable Data Pipelines**: Using AWS tools like Lambda, S3, and Glue to process, store, and manage data.
- **Work with Databases**: Integrating relational data (PostgreSQL on RDS) into a real-time workflow.
- **Create Insightful Dashboards**: Turning raw data into meaningful insights with QuickSight.

It’s a hands-on example of how I can apply my skills to build solutions that handle large-scale, dynamic workloads.

---

## 📋 How It Works

Here’s the step-by-step flow of the system:

1. **Vote Generation**:
   - Simulated voters generate votes, which are streamed to the `votes_topic` in Kafka (Amazon MSK).

2. **Real-Time Processing**:
   - A Lambda function consumes votes from Kafka and enriches them by querying voter and candidate details from RDS.
   - The enriched data is aggregated and sent to a separate Kafka topic (`aggregated_votes_topic`) and also stored in S3.

3. **Data Analytics**:
   - AWS Glue catalogs the processed data in S3, making it queryable with Athena.
   - Using Athena, I run SQL queries to analyze voting trends.

4. **Visualization**:
   - QuickSight connects to Athena and RDS to create live dashboards for visualizing the voting results.

---

## 🛠 How to Run the Project

### Prerequisites:
- **AWS Account** with access to services like MSK, RDS, Lambda, S3, Athena, and QuickSight.
- **Python 3.9+** installed locally.
- **AWS CLI** installed and configured.

### Steps:

1. **Set Up AWS Resources**:
   - Create an RDS PostgreSQL database and initialize the following tables:
     ```sql
     CREATE TABLE candidates (id SERIAL PRIMARY KEY, name VARCHAR(255), party VARCHAR(255));
     CREATE TABLE voters (id SERIAL PRIMARY KEY, name VARCHAR(255), age INT, region VARCHAR(255));
     CREATE TABLE votes (id SERIAL PRIMARY KEY, voter_id INT, candidate_id INT, timestamp TIMESTAMP);
     ```
   - Set up an Amazon MSK cluster and create Kafka topics:
     - `voters_topic`
     - `votes_topic`
     - `aggregated_votes_topic`
   - Create an S3 bucket to store processed voting data.

2. **Run the Producer**:
   - Simulate voting by running the Python producer script or AWS Lambda:
     ```bash
     python producer.py
     ```

3. **Run the Consumer**:
   - Process, enrich, and aggregate the votes using the Python consumer script or Lambda:
     ```bash
     python consumer.py
     ```

4. **Enable Analytics**:
   - Configure AWS Glue to crawl the S3 bucket and create a data catalog.
   - Use Athena to query aggregated voting data.

5. **Visualize Results**:
   - Connect QuickSight to Athena and create real-time dashboards.

---

## 📊 Dashboard

The final dashboard in QuickSight shows:
- Total votes received by each candidate.
- Regional breakdown of votes.
- Voter demographics and turnout trends.

This dashboard updates in real-time as new votes are processed.
---

## 📬 Let’s Connect!

If you’d like to chat about this project (or anything else), feel free to reach out:

- **LinkedIn**: https://www.linkedin.com/in/rkuturu/
