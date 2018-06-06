# Autoscaling - EC2 instances

# Challenge
Create an autoscaling group of web servers.  

They do not have to host anything of importance.  

My solution for this involves just using an Nginx proxy to proxy queries to /id to the instance metadata server and retrieve the instance id of the instance the serviced the call.

If you want more help, read the STEPS.md file

If you need even more help, check out the solution directory.  (THIS IS JUST ONE SOLUTION)

# Hands on!
Go terminate an instance in the autoscaling group.  Does the ASG replace the terminated server?  Did you expereince any service interruption?



