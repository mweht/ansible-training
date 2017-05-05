<h2>AWS IAM</h2>

<h4> IAM Essentials </h4>

IAM (Identity & Access Management) is where you manage your AWS users, groups and roles - and their access to AWS accounts and services.
- IAM provides access and access permissions to AWS Resources (Such as EC2, S3 and DynamoDB).
- IAM is global to all AWS Regions, so creating a user account will apply to al regions.

The common use of IAM is to manage:
- Users
- Groups
- Roles
- IAM access policies
- API Keys
- Passwords policies and MFA access

By default, any new IAM user you create in an AWS account is created with NO access to any AWS services. This is a non-explicit deny rule set on all new IAM users.

For all users (except root), permissions must be given that grant access to AWS services through IAM Policies.

When a new account is created, it is "best practice" to complete the task listed in IAM under "Security Status" - which include:
- Delete root access keys
- Activate MFA on the root account
- Create individual IAM users
- User groups to assign permissions
- Apply an IAM password policy

Other best practices include:
- Work as a user and never work with the root account.
- Apply the "Principal of least privilege" when managing AWS accounts, users, groups and roles.

---

<h4> IAM Policies </h4>

A policy is a document that formally states one or more permissions.
- By default, an **explicit deny** overrides an **explicit allow**.
- This allows for the use of a "deny all" policy to quickly restrict ALL access that a user may have through multiple attached policies.

IAM provides pre-built policy templates to assign to users and groups:
- Admin access: Full access to **ALL** AWS resources.
- Power user access: Admin access except for user/group management.
- Read only access: Only **READ** AWS resources

You can also create custom IAM permission policies using the **Policy Generator** or writing a policy from scratch.

More than one policy can be attached to a user group at the same time.

Policies cannot be directly attached to AWS resources (Such as an EC2 instance), you can use ROLES for that.

**IAM Policy example (admin access):**

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "*",
      "Resource": "*"
    }
  ]
}
```

---

<h4> IAM Groups </h4>

IAM Groups allow you to assign IAM permission policies to more than one user at a time.
This ability allows for easier access management to AWS resources.

Policies can be applied to a group containing multiple users instead of applying the same rule to each user individually.

---

<h4> IAM Roles </h4>

An IAM Role is a role that an AWS Resource (such as an EC2 instance OR a non-AWS account holder) can assume, and in doing so acquires the specific permissions defined by the role.
Roles are used because an policies cannot be applied to an AWS service/resource.

**POLICIES ARE ATTACHED TO A ROLE, AND AWS RESOURCES ASSUME ROLES**

For Example: If you are using an EC2 instance that needs to access an S3 bucket:
- Instance should assume a role from IAM with proper permissions (S3 Read-only).
- Instance  can then perform actions based on that role (read from S3 bucket).
- Credentials are better not stored on EC2 instances - so roles are used instead.
- An EC2 instance can only have ONE Role attached at a time.

Other uses for roles:
- Non-AWS users can assume a role for temporary access to AWS accounts and resources through having something like Active Directory or single sign-in services (Facebook, Google, etc).
- Create "Cross-Account" access where a user from one account can assume a role with permissions in another account.

---

<h4> IAM API Keys </h4>

API Access Keys are required to make programmatic calls to AWS from:
- AWS Command Line Interface (CLI)
- Tools for Windows PowerShell
- AWS SDKs
- Direct HTTP calls using the APIs for individual AWS services.

An example would be: API credentials used by developers, working from an on-premise network, for CLI Access.

Important API Keys facts:
- API Keys are only available **ONE TIME**, when a new user is created OR when you reissue a new set of keys.
- AWS will not regenerate the same set of access keys.
- In order for API credentials to work, they must be associated with a user.
- Roles does not have API Credentials.
- In the new AWS console you can only see the access key ID - Never the secret key ID.
- If you require new API credentials, you must deactivate the current set and generate a new one.
- It is NOT recommended to store API keys on EC2 instances.

