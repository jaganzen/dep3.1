<p align="center">
<img src="https://github.com/kura-labs-org/kuralabs_deployment_1/blob/main/Kuralogo.png">
</p>
<h1 align="center">C4_deployment-3<h1> 

# C4 Deployment Rollback Exercise Incident Report

## Table of Contents
1. [Purpose](#purpose)
2. [Issues](#issues)
3. [Steps](#steps)
4. [Optimization](#optimization)

## Purpose
Our Deployment posed an interesting challenge of simulating a scenario where we would essentially need to use version control to rollback an issue we had with a URL shortener tool. 

**Background**

We have an SLA with Nike to provide them access to our URL shortener. In the SLA, we are only allowed 20 minutes of downtime a year. If anything happens to the URL shortener, we must communicate any incidents to Nike.

### Nike's Use Case
- Nike uses special URLs called "launch pages" or "product pages" for new sneaker releases.
- These URLs are promoted through various channels such as website, social media, and email lists.
- Special functionalities like countdown timers and lottery systems are often involved in these pages.

**Resources Nike Uses**
- Website
- Social Media
- Email List

#### Additional Notes
Special URLs can:
1. Create a sense of exclusivity
2. Track customer behavior
3. Create a seamless customer experience

## Issues
One of the first issues we faced was that our Deployment 3.1 wasn’t deploying properly via Jenkins. This required us to rollback the application to an older version for troubleshooting.

## Steps

1. **Initial Build Issue**
    - Encountered "500 Internal Server Error"

2. **Rollback Steps**
    ```
    cd into our github repo via the command line
    cd deploy3.1
    cd c4_deployment-3.1
    git log --pretty=oneline
    git checkout 4eaf0baefef7d59bd6608711cfecc7fdfc030461 
    git add .
    git commit -m "Version 1 restored"
    git push
    git pull origin main
    git config pull.rebase false
    git status
    ```

3. **Resolving Test Phase Issue**
    - Update `test_app.py` as needed

<img width="778" alt="Screenshot 2023-09-23 at 8 40 21 AM" src="https://github.com/jaganzen/dep3.1/assets/101806502/cb29854e-613c-4fef-a248-112a3b64ff59">

<img width="1671" alt="Screenshot 2023-09-23 at 8 40 32 AM" src="https://github.com/jaganzen/dep3.1/assets/101806502/4713ec18-28d5-4aaa-b75d-a8009d8125dd">


## Replace Test Code Snippet in Python

Here is a Python test code snippet from our application.

```python
from application import app, greet

def test_quick():
  a = "jeff"
  greeting = greet(a)



<img width="785" alt="Screenshot 2023-09-23 at 8 40 40 AM" src="https://github.com/jaganzen/dep3.1/assets/101806502/fd38ed85-b1f4-49e2-a135-5b4dd7204ab0">


4. **Final Deployment**
    - URL Shortener is now working again.
  
![Screenshot 2023-09-22 at 10 50 38 PM](https://github.com/jaganzen/dep3.1/assets/101806502/0e441fe9-516f-4458-b1fd-6542d0f3db94)


## Optimization

**Problem Location**

- The issue originates at Line 20 with a discrepancy of one letter.

**Suggested Actions**

- Investigate the discrepancy and apply a fix in the next version.

