# rgbutterfly-site

![RGButterfly Logo](img/RGButterfly_Logo.png) _The iPhone App to Find Paint Swatches Associated with Areas in a Photo_

## Syncing Content with AWS

This Web site is currently hosted on _AWS Amazon_. It uses [_S3_](https://aws.amazon.com/s3/) for content and [_Route 53_](https://aws.amazon.com/route53/) for DNS management. I personally found this solution to be the most versatile and cost-effective for storage, hosting, and DNS management. Below are the steps for easily syncing content between the AWS S3 bucket and locally.

__Requirements__: _AWS (i.e., [LightSail](https://amazonlightsail.com)) Account, Python 2.7 or higher, and setup completed in the AWS Dashboard. For instructions on setting up DNS Hosted Zone (Route 53 Dashboard) and a Bucket with starter content (S3 Dashboard) visit the [AWS](https://aws.amazon.com) site_.

### Mac OS (UNIX) Setup

#### Installing PIP (check first if available)

* cd /tmp; curl -O https://bootstrap.pypa.io/get-pip.py
* python get-pip.py --user
* export PATH=~/Library/Python/2.7/bin:$PATH (or correct version/location). Might want to add the _export_ statement in the .bashrc)
* pip install --user --upgrade awscli
* mv get-pip.py ~/Library/Python/2.7/bin (or remove, as probably wont need this any longer)

#### Setting up the AWS Configuration

* If not done, clone your initial empty, except perhaps for the README.md, project (i.e., git clone https://github.com/spineo/rgbutterfly-site.git) and cd into that site
* Go to your AWS dashboard and, under your account section drop-down, click on _My Security Credentials_
* Click on _Access Keys_ to uncollapse that section and the _Create New Access Key_ button to generate a _Access Key ID_ and _Secret Access Key_)
* Back on the shell window, run _aws configure_ and enter the Access Key ID and Secret Access Key created earlier. Make sure that you also specify the correct _Default region name_ (i.e., us-east-1 or whatever region you are hosted under) and leave the _Default output format_ set to "None" for now

#### Using the AWS CLI

* The first thing you will need is your site _bucket name_. This can be obtained from your _AWS S3_ dashboard
* You will want to initially sync the starter content from S3 locally (where the project was cloned) by running _aws s3 sync s3://bucket name/ ._
* Next, make sure you add/commit and push content to GitHub (i.e., _git add \*_ and _git commit \*_)
* To upload changes or new content run _aws s3 cp local-dir-or-file s3://bucket name/_

#### References
* [AWS CLI Command Reference](http://docs.aws.amazon.com/cli/latest/reference/s3/)

