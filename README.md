# aws-eb-cron
Makes it easy &amp; safe to run cron tasks on just the leading instance in an Elastic Beanstalk cluster.

Usage:
- Add the AmazonEC2ReadOnlyAccess policy to the aws-elasticbeanstalk-ec2-role (required so that instances can check their status)
- Drop the `10_aws_eb_cron.config` file into your `.ebextensions` folder within your project.
- Prefix cron tasks with `aws-eb-cron` when you only want them to run on the leading instance.
- The script will periodically check if it is on the active leader, making this safe to use when scaling up and down.

Example: Every 5 minutes, execute `php cron.php`, but only do so on one instance in the beanstalk environment.
```
*/5 * * * * root aws-eb-cron php cron.php
```
