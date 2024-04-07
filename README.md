# AWS Cloud Cost Optimization - Identifying Stale Resources

## Identifying Stale EBS Snapshots

In this example, we'll create a Lambda function that identifies EBS snapshots that are no longer associated with any active EC2 instance and deletes them to save on storage costs.

### Description:

The Lambda function fetches all EBS snapshots owned by the same account ('self') and also retrieves a list of active EC2 instances (running and stopped). For each snapshot, it checks if the associated volume (if it exists) is not associated with any active instance. If it finds a stale snapshot, it deletes it, effectively optimizing storage costs.

### Procedure:

1. Go to the AWS Management Console and navigate to AWS Lambda.

2. Click on "Create function" and choose "Author from scratch".

3. Name your Lambda function and select the runtime (e.g., Python, Node.js) that matches your code.

4. In the code editor, either paste the code provided in my repository or upload the code file.

5. Configure the execution role for your Lambda function. Create a new role if needed and attach the following policies:
    - First policy: Permissions for snapshots, including "DescribeSnapshots" and "DeleteSnapshot".
    - Second policy: Permissions for instances and volumes, including "DescribeInstances" and "DescribeVolumes".

6. Once the role and policies are configured, complete the Lambda function creation process.

7. After creating the Lambda function, integrate it with Amazon CloudWatch to schedule its execution. 
    - Go to CloudWatch in the AWS Management Console.
    - Navigate to "Rules" under "Events".
    - Click on "Create rule" and choose the service to schedule the Lambda function.
    - Set the schedule (e.g., cron expression) for when you want the function to run.
    - Configure the target as the Lambda function you created.

8. Save the rule, and now your Lambda function will automatically execute according to the schedule set in CloudWatch.

By following these steps, you'll have a Lambda function set up to identify and delete stale EBS snapshots, helping to optimize your AWS cloud costs.
