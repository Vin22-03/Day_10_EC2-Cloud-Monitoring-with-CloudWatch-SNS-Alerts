# 🚨 EC2 Cloud Monitoring with CloudWatch + SNS Alerts

This project simulates a real-world Cloud Engineer task: setting up **proactive monitoring** and **email alerts** for an EC2 instance using **Amazon CloudWatch + SNS**.

---

## 🎯 Objective

Detect performance issues before users do.

We configured CloudWatch to monitor:
- 🧠 Memory Usage
- 💽 Disk Usage
- ⚙️ CPU Usage

And receive 🔔 email notifications via **Amazon SNS** when thresholds are breached (e.g., memory > 15%).

---

## 🧰 Tools Used

| Tool             | Purpose                                 |
|------------------|-----------------------------------------|
| **EC2 (Ubuntu)** | Monitored instance                      |
| **CloudWatch**   | Metrics & alarms                        |
| **CloudWatch Agent** | Push memory/disk/CPU metrics         |
| **SNS**          | Send email alerts                       |
| **IAM Role**     | Allow EC2 to publish metrics            |

---

## 🛠️ Setup Steps

### 1. Launch EC2 with IAM Role:
- Create IAM Role: `CloudWatchAgentServerPolicy`
- Attach role to EC2 instance

### 2. Install & Start CloudWatch Agent:
```bash
wget https://s3.amazonaws.com/amazoncloudwatch-agent/ubuntu/amd64/latest/amazon-cloudwatch-agent.deb
sudo dpkg -i amazon-cloudwatch-agent.deb
```
### 3. Create Configuration File.
### 4. Start the CloudWatch Agent.
### 5.📊 Create CloudWatch Alarm
- Go to CloudWatch → Alarms → Create Alarm

- Choose metric: mem_used_percent

- Set threshold: > 15% (for testing)

- Period: 1 minute

- Action: send to SNS Topic

### 6.📧 Set Up SNS for Email Alerts
- Go to SNS → Topics → Create topic

- Name it: EC2MonitoringAlerts

- Create a subscription to your email

- Confirm via your inbox

### ✅ Outcome
- When memory usage exceeded the threshold, SNS sent an email alert successfully.

- This shows how real-time monitoring and proactive incident response works on AWS.
  
### 🧠 Learning Takeaways
- Install and configure the CloudWatch Agent

- Monitor CPU, memory, and disk usage

- Create custom CloudWatch Alarms

- Trigger real-time notifications with SNS

- Think like a CloudOps/SRE engineer 🧩

