# schedule-ec2-instances-managed-by-autoscalinggroups

Many times, we have a lot of cloud waste because we never shut down our services/EC2 instances. One of the most
challenging cases is to schedule those instances that belong to an Autoscaling Group.

To Begin you must create two Lambda functions:

1. One for **stopping** that is going to have a **0** as the environment variables (MIN_SIZE, MAX_SIZE and DESIRED_CAPACITY).

2. One for **starting** that is going to have a **+1** as the environment variables (MIN_SIZE, MAX_SIZE and DESIRED_CAPACITY).


# Create new Lambda function for (Start/Stop) Event

you can find the lambda functions that you gonna use for start and stop the instances in thz main directory : **start-instances.py** and **stop-instances.py**.

after you create the lambda functions you must assign for them a policy that give the access to the autoscaling groups and also also allow them to create log groups in cloudwatch (you find the policy in the file : **iam-role.json**).

Now for scheduling those lambda fuctions you need associate for each one of them to an eventBridge rule.

