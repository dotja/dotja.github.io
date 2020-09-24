---
layout: post
date: 2020-09-24
category: devops
title: Configure AWS S3 for Static Storage in Django
summary: "How to create an S3 bucket and configure it to be used in a Django app"
---
<div media:type="text/omd" class="blog_title_style container">
    <h1><span>Configure AWS S3 for Static Storage in Django</span></h1>
    <small>24 September 2020</small>
</div>

<div media:type="text/omd" class="blog_content_style container">

<p id="blog_text">
<kbd>S3</kbd> or Simple Storage Service is a type of cloud storage where you access your data over the internet. It is an object-storage service where files are stored as objects rather than in a filesystem structure.
</p>

<p id="blog_text">
An S3 bucket is a container or a top-level folder that is used to store objects. An object consists of data, metadata and an identifier. It might appear that S3 buckets store files as folders because there is a slash in the file name, but that is not the case.
</p>

<p id="blog_text">
Storing you site's static files in S3 frees up your server from handling more static requests. And it is also used in case you are choosing the AWS Lambda or other serverless architectures for your site.
</p>


<p id="blog_text">
In this article, I will assume that you already have an AWS IAM (Identity and Access Management) user setup with a group. This user has AmazonS3FullAccess permission and it also has a Key ID and a secret.
</p>


<h3 id="blog_text">I. Create an S3 Bucket</h3>
<ol id="blog_text">
    <li>Go to the S3 service in the services menu</li>
    <li>Click "Create bucket"</li>
    <li>Add a name for your bucket and click "Next"</li>
    <li>Keep the default options and click "Next"</li>
    <li>Click "Create bucket"</li>
</ol>


<h3 id="blog_text">II. Edit the CORS Permissions</h3>

<p id="blog_text">
CORS (cross-origin resource sharing) allows web apps from different domains to have access to the S3 resources.
<br>
To edit it, go to the "Permissions" tab and choose "CORS configuration" and add the rule below and save.
</p>

<pre>
&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;CORSConfiguration xmlns="http://s3.amazonaws.com/doc/2006-03-01/"&gt;
    &lt;CORSRule&gt;
        &lt;AllowedOrigin&gt;*&lt;/AllowedOrigin&gt;
        &lt;AllowedMethod&gt;GET&lt;/AllowedMethod&gt;
        &lt;MaxAgeSeconds&gt;3000&lt;/MaxAgeSeconds&gt;
        &lt;AllowedHeader&gt;*&lt;/AllowedHeader&gt;
    &lt;/CORSRule &gt;
&lt;CORSConfiguration &gt;
</pre>

<div class="centered_div">
<img style="width:100%;" class="" src="/assets/images/s3_1.png">
</div>

<p id="blog_text">
<strong>AllowedOrigin</strong> is used to specify the origin we want to allow cross-domain requests from.
<br>
<br>
<strong>AllowedMethod</strong> can be GET, PUT, POST, DELETE or HEAD.
<br>
<br>
<strong>MaxAgeSeconds</strong> is the amount of time in seconds that the browser caches the response obtained.
<br>
<br>
<strong>AllowedHeader</strong> specifies the headers allowed in the request header.
</p>


<h3 id="blog_text">III. Edit the Bucket Policy</h3>
<p id="blog_text">
Given that the bucket has Public access enabled, we need to create a policy that would only grant read access to the static files in the bucket. Therefore in the "Permissions" tab under "Bucket Policy", add the following policy:
</p>

<pre>
{
  "Version":"2012-10-17",
  "Statement":[{
    "Sid":"PublicReadGetObject",
      "Effect":"Allow",
      "Principal": "*",
      "Action":["s3:GetObject"],
      "Resource":["arn:aws:s3:::my_bucket_name/*"
      ]
    }
  ]
}
</pre>

<div class="centered_div">
<img style="width:100%;" class="" src="/assets/images/s3_2.png">
</div>

<p id="blog_text">
<strong>Version</strong> is the latest defined policy language version.
<br>
<br>
<strong>Sid</strong> is the statement id which identifies the policy statement.
<br>
<br>
<strong>Effect</strong> can be Allow or Deny.
<br>
<br>
<strong>Principal</strong> used to specify the user.
<br>
<br>
<strong>Action</strong> is the action to be allowed or denied.
<br>
<br>
<strong>Resource</strong> are the objects that this policy concerns using "arn" or the Amazon Resource Name.
</p>


<h3 id="blog_text">IV. Configure your Django App to use S3</h3>
<p id="blog_text">
In development environments, Django typically would be configured to use the local filesystem for storing static files. To start using your S3 bucket, install the 2 modules below:
</p>

<pre>
pip install boto3
pip install django-storages
</pre>

<p id="blog_text">
After that you need to add "storages" in your settings files under the installed apps.
</p>

<pre>
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'rest_framework',
    'storages',
    'my_app',
]
</pre>


<p id="blog_text">
Define the environment variables below and then use them from your settings file as to avoid pushing code to version control that has sensitive information.
</p>

<pre>
<span class="code_comments">## in your setting.py add:</span>

AWS_STORAGE_BUCKET_NAME = os.getenv('AWS_STORAGE_BUCKET_NAME')
AWS_SECRET_ACCESS_KEY = os.getenv('AWS_SECRET_ACCESS_KEY')
AWS_ACCESS_KEY_ID = os.getenv('AWS_ACCESS_KEY_ID')
AWS_S3_CUSTOM_DOMAIN = os.getenv('AWS_S3_CUSTOM_DOMAIN')

STATIC_URL = 'https://my_bucket_name.s3.eu-west-2.amazonaws.com/'
STATICFILES_DIRS = [ os.path.join(BASE_DIR, 'static') ]
STATICFILES_STORAGE = 'storages.backends.s3boto3.S3Boto3Storage'
</pre>

<p id="blog_text">
After that, you can upload your static files into the bucket using the AWS console interface or programmatically by typing the command below in your terminal:
</p>

<pre>
python manage.py collectstatic
</pre>

<p id="blog_text">
To verify that your website is now using S3, you can inspect an image or look in the page's source code.
</p>

</div>


