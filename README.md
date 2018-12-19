# aws-eb-cron
Makes it easy &amp; safe to run cron tasks on just the leading instance in an Elastic Beanstalk cluster.

Usage:
- Add the AmazonEC2ReadOnlyAccess policy to the aws-elasticbeanstalk-ec2-role (required so that instances can check their status)
- Drop the `.config` file into your `.ebextensions` folder within your project.
- Execute cron tasks with `aws-eb-cron` in front of them.

Example: Every 5 minutes, execute `php cron.php`, but only do so on one instance in the beanstalk environment.
```
*/5 * * * * root aws-eb-cron php cron.php
```
