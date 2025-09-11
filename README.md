# AWS Resource Dashboard (Flask + Boto3)

This project provides a simple **Flask web application** that displays
AWS resources such as: - Running **EC2 Instances** - Configured
**VPCs** - **Load Balancers** (ALB/NLB) - **AMIs** owned by the account

The app fetches data from AWS using **boto3** and renders it in a
browser-friendly HTML table.

------------------------------------------------------------------------

## 📖 Background

Managing AWS resources often requires using the AWS Console or CLI. This
project demonstrates how to: - Use **Flask** to serve a lightweight web
dashboard. - Use **boto3** to interact with AWS services
programmatically. - Leverage **environment variables** for credentials
(no hardcoding sensitive values). - Run the app locally in a Python
**virtual environment (venv)**.

This makes it a useful starting point for **cloud admins, DevOps
engineers, or learners** exploring AWS automation.

------------------------------------------------------------------------

## ✅ Requirements

-   Python **3.8+**
-   AWS account with the following permissions:
    -   `ec2:DescribeInstances`
    -   `ec2:DescribeVpcs`
    -   `ec2:DescribeImages`
    -   `elasticloadbalancing:DescribeLoadBalancers`
-   Local environment with `pip` and `venv` available.

------------------------------------------------------------------------

## ⚙️ Setup Instructions

### 1. Clone the Repository

``` bash
git clone https://github.com/yhayat1/jbh-aws-module-project.git
cd jbh-aws-module-project
```

### 2. Create & Activate Virtual Environment

On Linux/macOS:

``` bash
python3 -m venv .venv
source .venv/bin/activate
```

On Windows (PowerShell):

``` powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### 3. Install Dependencies

Using the `requirements.txt` file:

``` bash
pip install -r requirements.txt
```

### 4. Export AWS Credentials

Set your AWS keys and region as **environment variables**:

On Linux/macOS:

``` bash
export AWS_ACCESS_KEY_ID=YOUR_KEY_ID
export AWS_SECRET_ACCESS_KEY=YOUR_SECRET
```

On Windows (PowerShell):

``` powershell
$env:AWS_ACCESS_KEY_ID="YOUR_KEY_ID"
$env:AWS_SECRET_ACCESS_KEY="YOUR_SECRET"
```

### 5. Run the Application

``` bash
python python/app.py
```

Then open <http://127.0.0.1:5001> in your browser.


## 📝 How It Works

1.  Flask starts a local web server on **port 5001**.
2.  On each request to `/`, boto3 fetches:
    -   EC2 instances (`describe_instances`)
    -   VPCs (`describe_vpcs`)
    -   Load balancers (`describe_load_balancers`)
    -   AMIs (`describe_images`)
3.  Data is rendered into an HTML table with Jinja2 templates.
4.  The result is shown in your browser.

------------------------------------------------------------------------

## 🔐 Security Notes

-   Never commit your **AWS_ACCESS_KEY_ID** or **AWS_SECRET_ACCESS_KEY**
    to GitHub.
-   Use **IAM users/roles** with the least privileges required.
-   Consider using **AWS CLI profiles** instead of plain env vars for
    long-term setups.

------------------------------------------------------------------------

## 🚀 Next Steps (Optional Enhancements)

-   Filter resources by **tags** (e.g., show only `Environment=Prod`).
-   Add authentication to the web UI.
-   Deploy to a container (Docker) or serverless platform.
-   Extend support for more AWS services (S3, RDS, etc.).

------------------------------------------------------------------------

## 📜 License

MIT License. Free to use and modify.
