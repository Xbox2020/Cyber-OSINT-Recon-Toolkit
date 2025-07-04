
# 🔐 Flask Vulnerability Audit & Hardening Project
Welcome to the Flask Vulnerability Audit & Hardening project! 

# 1. About the repo
🛡️ This beginner-friendly project walks through building a deliberately insecure web app, identifying key vulnerabilities (based on the OWASP Top 10), and then fixing them with proper security controls. Ideal for your cybersecurity portfolio!

### Dashboard Link : https://app.powerbi.com/groups/me/reports/384d017e-e935-44dc-9e7d-1626c1a36de1/ReportSection
________________________________________
## 🎯 Problem Statement
Many beginner web apps lack secure handling of sensitive data and user access control. This project demonstrates the dangers of such design and how to correct them.
 
________________________________________

## 📌 Project Overview

| **Section**                    | **Content**                                                                 |
|-------------------------------|------------------------------------------------------------------------------|
| Vulnerable Code (commit 1)    | Plain Flask app with issues                                                 |
| Audit Report                  | README explaining vulnerabilities, OWASP tags, CLI proof, screen GIFs       |
| Fixed Code (commit 2)         | Secure logic, hashed DB, removed bugs                                       |
| Automated Tests               | PyTest ensuring fixes work                                                  |
| Assets                        | `/gifs`, `/screenshots`, README embedded visuals                            |
| Instruction                   | How to run, replicate audit, and improve                                    |


________________________________________


### ⚙️ Requirements
###
•	Python 3.7+
•	Flask
•	bcrypt
•	PyTest
________________________________________

# 2. Step by Step
### 💻 Installation & Setup	
#### 1. Set up the Environment	
With your account, download and connect all related file.



#### 2. Clone the repo	
Using the URL below, on the linked Repo, run the following;
https://github.com/yourusername/flask-vuln-harden.git

						cd flask-vuln-harden
						python3 -m venv venv
						source venv/bin/activate
						pip install -r requirements.txt

# 3. Start & Test  the app
						python app.py
________________________________________
 
### Steps followed 🧪

- Step 1 : Created insecure app (commit 1)
  
  (a) Stored passwords in plaintext 🧨
  
  (b) No proper access control 🚪
  
  (c) No input validation 🖊️
  
Before Screenshot: 


- Step 2 : Identified Vulnerabilities 🕵️‍♀️
  
  (a) Broken Access Control 🧨🧨
  
  (b) Insecure Direct Object References (IDOR) 🚪🚪
  
  (c) Sensitive Data Exposure 🖊️🖊️

	



________________________________________
### 🔍 Audit Table

| **OWASP Category**                       | **Description**         | **Found In**              |
|------------------------------------------|--------------------------|----------------------------|
| A01:2021 - Broken Access Control         | Admin toggle via URL     | `/dashboard?admin=true`   |
| A02:2021 - Cryptographic Failures        | Plaintext password       | `app.py`                   |
| A05:2021 - Security Misconfiguration     | No CSRF token            | Forms                      |




3. Hardened the app (commit 2)
•	✅ Implemented bcrypt password hashing
•	✅ Added user role-based control
•	✅ Validated all inputs with WTForms
After Screenshot: 
4. Added Automated Tests 🧪
pytest
Sample Test Snippet:
def test_password_hashed():
    assert not 'password123' in get_user_db_password()
5. CI Workflow 🌀
GitHub Actions Workflow .github/workflows/main.yml
name: Flask App Test
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Setup Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.10'
      - run: pip install -r requirements.txt
      - run: pytest
________________________________________
💡 Side Notes & Developer Insights
•	🎓 This project is built for learning. Vulnerabilities are included intentionally.
•	🔁 Split commits to show vulnerable → secure evolution.
•	📚 OWASP Top 10 used as the audit framework.
•	🧰 Future Add-ons:
o	Bandit/Flake8 static code analysis
o	Docker container with default weak settings
o	Role-based access matrix
________________________________________
📸 Visual Gallery
Before Fix	After Fix
	
	
________________________________________
📹 Video Walkthrough
________________________________________
📜 Scripts & Code Snippets
Plaintext Password (Bad):
users[username] = password  # 😬 insecure
Hashed Password (Fixed):
hashed = bcrypt.hashpw(password.encode('utf-8'), bcrypt.gensalt())
users[username] = hashed
Broken Access (Bad):
if request.args.get('admin') == 'true':
    return render_template('admin.html')
Role-Based Access (Fixed):
if current_user.role == 'admin':
    return render_template('admin.html')
________________________________________
✅ Key Takeaways
•	Understand how OWASP Top 10 flaws appear in small web apps
•	Practice auditing and fixing real-world vulnerabilities
•	Learn Python, Flask, bcrypt, and PyTest
•	Demonstrate CI/CD integration for security workflows
________________________________________
🛠️ Try It Yourself
1.	Clone the repo
2.	Install dependencies
3.	Run the vulnerable version
4.	Walk through README
5.	Harden it and contribute fixes 🎉
________________________________________
👏 Credits
This repo is designed for learning purposes and project portfolios. Inspired by real-world vulnerabilities and built for junior security analysts.
________________________________________
Feel free to fork and improve! 💪
