**IAM GROUP POLICY UTILIZATION**

![alt text](https://github.com/tanersa/iamgrouppolicies/blob/master/sharksIAM/IAM.png)

In order for users to utilize AWS services, we must create IAM policies for IAM user groups then attach those policies to those user groups.

There are 4 IAM resources to create an IAM group policy in "**Best Practice**". 

1. User groups
2. Users
3. Roles
4. Policies/Permissions

==========================================================================================

1) First, user groups should be created to be attached to policies later.
    - Click "Create Group" button on upper right hand side of the screen.
    - Name your group as needed to define group of users. 
    - Scroll all the way down and click "Create Group" button lower right hand side corner after skipping optional sections on the page. 

2) Secondly, policies are needed to be generated for defined user groups. 
    - Click on "Policies" then hit "Create Policy"
    - Hit JSON tab as a second tab available.
    - For inline policy json file, use "AWS Policy Generator" (https://awspolicygen.s3.amazonaws.com/policygen.html) to generate policy based on the requirement. 
     - **_For_instance_**; In order to give EC2 service access:
     Select policy type as IAM policy
     Effect should be "Allow"
     AWS Service, choose "Amazon EC2"
     Actions section, only "DescribeVolumes", "Get", or "List" related items can be chosen if only read access is being given
     Only DevOps can have Start/Stop access.
     Amazon Resource Name section, * can be placed for basic IAM policy creation
     Then hit "Add Statement" button 
     Lastly, click on "Generate Policy" button to generate your own policy which will be inline policy. 
     Then copy the json file and close the modal on the page. 
    - Next, go back to create policy page for pasting JSON file that we just copied lately.
    - Click on "Next: Tags"
    - Hit "Next Review" and name the policy on next page.
    - Describe your policy to adress correct needs.
    - Lastly, click on "Create Policy" button.
    - Then we should see our new policy created on the screen.
    - Type would be "Customer Managed" since we created our own policy.
    - With this access we give access to all EC2 (Elastic Cloud Compute Service) instances.
    - Additionally, we gave access to all resources globally not just in the region because IAM is a global entity.
    
**_Important_Notes_:** Do not give "DescribeHosts" action to the user who has only read access. We should only give access what is necessary and minimal. Otherwise, it would not be best practice. That may create security vulnerability risk easily. 

3) Now, users are missing, so we are in the process of adding users to user groups.
    - Go to "Users", then click on "Add User", name the user. 
    - Check the checkbox for "Password-AWS Management Console Access"
    - Choose "Custom password" then place your password. 
    - You may want to uncheck the checkbox for "Require password reset" in order to avoid for resetting the pwd every time you login. 
    - Hit "Next: Permissions" button. 
    - Choose "Add User to group"
    - Choose users to be added to the same group just created. 
    - Click on "Next: Tags"
    - Click on "Next: Review"
    - Lastly hit "Create User"
    - New User should be created and "Success" message is on the screen.
    - Hit on "Close" button. 



4) Next step is that we need to attach above policies to user groups (not individual users) we just created. That means we are putting our policy in operation.
    - Go to "Policies" then check the radio button next to policy you would like to attach
    - Extend the "Actions" drop-down and choose Attach option..
    - Choose the group you want to attach. Then click on Attach policy.
    - Now policy is attached and on operation. 
    - Policies page would show this policy is used as "Permission Policy". 


All the users including newly created ones should be on the screen. Then go to user groups page and that also should include newly created user groups. 

Note[^1].
[^1]: In order to test if those users have privilige for correct access, you may want to login as those users and verify their access.
      Read only users should not be able to start/stop the instances. Whereas admin or DevOps users would have that privilige.




















































