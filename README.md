# task-7
ELB-AUTOSCALING
In this task, I created a simple HTML web page titled “Cloud Auto Scaling Demo”, which displayed the message “Hello from my Cloud Instance!” and was hosted on multiple AWS EC2 instances.
I launched two (t2.micro) Ubuntu VMs and installed Apache Web Server using the commands
sudo apt update, sudo apt install apache2 -y, and sudo systemctl start apache2.
The index.html file was copied to /var/www/html/ on each instance.

Next, I configured an Application Load Balancer (HTTP type) to distribute traffic to these instances on port 80, with a health check also defined on port 80.
The Load Balancer provided a public URL that successfully displayed the hosted web page from any connected backend instance.

After that, I created an Auto Scaling Group using the same VM template, setting the minimum = 1, desired = 2, and maximum = 4 instance limits.
The scaling policy was based on CPU utilization > 60%, so when load increased, additional instances were automatically launched, and when demand dropped, excess instances were terminated.

Finally, I tested the configuration using a load-testing command
ab -n 500 -c 50 http://<load-balancer-URL>/
to simulate heavy traffic and observed the Auto Scaling Group adding instances automatically.
This task demonstrated how AWS Auto Scaling and Load Balancing maintain high availability, scalability, and cost efficiency in cloud-hosted applications.
