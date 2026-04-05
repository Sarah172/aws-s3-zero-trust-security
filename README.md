# AWS S3 Security Hardening (End-to-End)

> A real-world cloud security project implementing IAM policies, S3 bucket policies, encryption, logging, and monitoring to fully secure an S3 environment.

---

## Overview

In this project, I secured an S3 bucket for a production-like environment by enforcing:

- Least privilege access  
- Folder-level user isolation  
- IP-based access restrictions  
- Encryption enforcement  
- Activity logging and monitoring  
- Real-time alerting on destructive actions  
- Complete public access blocking  

---

## Architecture

IAM Users → IAM Policy → S3 Bucket Policy → S3 

↓

CloudTrail → CloudWatch → SNS Alerts


---

## Technologies Used

- Amazon S3  
- AWS IAM  
- AWS CloudTrail  
- Amazon CloudWatch  
- Amazon SNS  
- AWS CLI  

---

## Implementation (With Screenshots)

### 1. Create & Modify IAM Policy

![Policy Overview](screenshots/Picture41.png)

![Policy JSON](./screenshots/Picture42.png)

![Policy Conditions](./screenshots/Picture43.png)

---

### 2. Confirm Policy Update

![Policy Updated](./screenshots/Picture45.png)

---

### 3. Configure CloudTrail Logging

![CloudTrail](./screenshots/Picture46.png)

![CloudWatch Logs](./screenshots/Picture47.png)

---

### 4. Configure SNS Notifications

![SNS Setup](./screenshots/Picture50.png)

![SNS Confirmed](./screenshots/Picture51.png)

---

### 5. Create EventBridge Rule for Monitoring

![EventBridge Rule](./screenshots/Picture52.png)

---

### 6. Attach Policy to IAM Groups

![IAM Groups](./screenshots/Picture56.png)

---

### 7. Verify CLI Access

![CLI Access](./screenshots/Picture57.png)

---

### 8. Create Folder-Based Access Structure

![Folders](./screenshots/Picture59.png)

---

### 9. Test Access Restrictions

#### ❌ Unauthorized Access

![Access Denied](./screenshots/Picture60.png)

---

### 10. Test Delete Permissions

![Delete Test](./screenshots/Picture61.png)

---

### 11. Enforce Encryption

![Encryption](./screenshots/Picture62.png)

---

### 12. Block Public Access

![Block Public](./screenshots/Picture63.png)

---

## Results

- Public access completely blocked  
- Users restricted to their own folders  
- Cross-user access denied  
- Encryption enforced on uploads  
- Alerts triggered on object deletion  
- Full logging enabled  

---

## Key Takeaways

- **Defense in Depth is Essential**  
  Combining IAM, bucket policies, logging, and monitoring creates strong security.

- **IAM + Bucket Policies Work Together**  
  IAM defines identity permissions, bucket policies enforce environmental controls.

- **Dynamic Access Control is Powerful**  
  `${aws:username}` enables scalable folder-level isolation.

- **Monitoring is Critical**  
  CloudTrail + CloudWatch + SNS ensures full visibility.

- **Security Must Be Enforced at Upload Time**  
  Encryption policies prevent insecure data storage.

---

## Lessons Learned

- **S3 Security Requires Multiple Layers**  
  No single service provides full protection.

- **Policy Misconfiguration is Risky**  
  Small JSON errors can break or overexpose access.

- **Testing with CLI is Crucial**  
  It reveals real-world permission behavior.

- **Delete Permissions Must Be Carefully Scoped**  
  Prevents accidental or malicious data loss.

- **Public Access Settings Are Not Enough Alone**  
  Must be combined with policies for full protection.

---

## Challenges

- Writing complex IAM JSON policies  
- Debugging permission errors  
- Understanding AWS policy evaluation logic  
- Configuring event-driven monitoring  

---

## Recommendations

- Use IAM roles instead of users  
- Enable MFA for all users  
- Integrate AWS Security Hub  
- Add automated remediation with Lambda  
- Use VPC endpoints for S3 access  

---

## Project Structure

├── README.md
├── screenshots/
│ ├── core/
│ └── full/

