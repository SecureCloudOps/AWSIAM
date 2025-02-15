# Securing the Cloud: AWS IAM Best Practices

**Author:** Mohamed Mohamed  
**Email:** mohamed0395@gmail.com

---

![Image](https://i.imgur.com/OaHxJev.png)

---

## Introducing today's project!

### What is AWS IAM?

AWS IAM is a service that controls who can access your AWS resources and what they can do. It's essential for security by letting you create users, assign permissions, and protect your AWS account from unauthorized access.

I used AWS IAM in today's project by creating group policies and an alias user.
This project took me one hour and a half to complete.

---

## Tags

Tags are like labels you can attach to AWS resources for organization. They are useful because it helps us with identifying all resources with the same tag at once.

The tag I’ve used on my EC2 instances is called Env. The values I've assigned for my instances are production and development.

![Image](https://i.imgur.com/V52YZp1.png)

![Image](https://i.imgur.com/p3dAkYw.png)

![Image](https://i.imgur.com/3M2TKtS.png)

---

## IAM Policies

IAM policies are JSON documents in AWS that define permissions for users, roles, and groups. They specify allowed or denied actions on AWS resources using effect, action, resources, and condition statement.

### The policy I set up

For this project, I’ve set up a policy using JSON

I’ve created a policy that allows managing EC2 instances tagged `Env = development` and `Env = production`while preventing unauthorized tagging changes. It ensures controlled access to development instances and blocks users from modifying tags.

### When creating a JSON policy, you have to define its Effect, Action and Resource.

The Effect, Action, and Resource attributes of a JSON policy mean: Effect defines whether to allow or deny actions, Action specifies the permitted or denied operations, and Resource determines which AWS resources the policy applies to.

---

## My JSON Policy

![Image](https://i.imgur.com/iAw4KVc.png)

---

## Account Alias

An account alias is a user-friendly name for an AWS account, making it easier to remember than the default 12-digit account ID. It can be used in the AWS login URL instead of the account ID.

Creating an account alias took me just a few seconds. Now, my new AWS console sign-in URL is **https://project-alias-mohamed.signin.aws.amazon.com/console**, making it easier to access my account without remembering the 12-digit account ID.

![Image](https://i.imgur.com/ba8tDhM.png)

---

## IAM Users and User Groups

### Users

IAM users are individual indentities in AWS with specific credentials (passwords, access keys) used to interact with AWS services. They can be assigned permissions directly or through groups to control access to resources.

### User Groups

IAM user groups are collections of users that share the same permissions. Policies attached to a group apply to all its members, simplifying access management without assigning permissions individually.

I attached the policy I created to this user group, which means all users in that group inherit the permissions defined in the policy. This simplifies access management, ensuring consistent permissions without assigning policies to each user individually.

---

## Logging in as an IAM User

The first way is to share the sign-in URL username, and temporary password via email. The second way is to provide the details manually or through a secure communication channel like a company-approved password manager.

Once I logged in as my IAM user, I noticed that I was already seeing Access denied on my dashboard panels. This is because my IAM user hasn't been granted the necessary permission to view these resources.

![Image](https://i.imgur.com/jO1QRPw.png)

---

## Testing IAM Policies

I tested my JSON IAM policy by trying to delete an instance (production instance) with my development user.

### Stopping the production instance

When I tried to stop the production instance, a red banner told me that I was not authorized. I didn't have the required permissions to stop the instances with the production tag.

![Image](https://i.imgur.com/dg08yBQ.png)

---

## Testing IAM Policies

### Stopping the development instance

Next, when I tried to stop the development instance, it was successful because it had the right permissions and tags.

![Image](https://i.imgur.com/qYlcbAb.png)

---

## The IAM Policy Simulator

The IAM Policy Simulator is a tool for testing and validating IAM policies. Its useful for ensuring permissions are correctly configured, troubleshooting access issues and identifying security risks before applying policies in a live AWS environment. 

![Image](https://i.imgur.com/OaHxJev.png)

---

---
