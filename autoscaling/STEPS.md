# Steps to create an autoscaling group of EC2 servers

There are probably 100's of ways of doing this.  This is just one way.

## High Level Steps
1. Create an AMI of the server you want to boot.
1. Create a launch configuration launching that AMI
1. Create an autoscaling group based on that launch config

## Detailed Steps
### Create an AMI
1. Boot up a linux server.  I am using an amazon linux server.
1. SSH into that server.
1. sudo yum install nginx
1. sudo vi /etc/nginx/conf.d/virtual.conf  and put the following data in the file 
	```
	server {
    	listen       80;
    	server_name  *.amazonaws.com *.ec2.internal localhost;

    	location /id {
		proxy_pass http://169.254.169.254/latest/meta-data/instance-id;
    		}
	}
	```
1. sudo service nginx start
1. curl http://[DNS NAME OF HOST]/id
1. sudo chkconfig nginx on
1. reboot your server to verify that it works after a reboot.  re-execute the curl statement to verify.
1. From the Control Panel create an image from the server.  (This may take a few minutes to complete - make sure you have the option to reboot the server - that ensures a good snapshot.  This is a check-box that should NOT be selected (checking is NO REBOOT)
1. Create an ALB
1. Create a Launch Configuration
1. Create Autoscaling group. Configure to recieve traffic from the ALB.  set min size to 1, max to 3, and scale if an instance gets more than 3 requests. Use EC2 status as the health check. Tag new instances with a name you will recognize.
1. 


