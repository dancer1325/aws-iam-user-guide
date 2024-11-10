# IAM Identities \(users, user groups, and roles\)<a name="id"></a>

* ways to sign in to AWS
  * as the AWS account root user
  * as an IAM user
  * with your IAM Identity Center user
    * -- via the -- sign-in URL / -- was sent to -- your email address | create IAM Identity Center user
    * see [Signing in to the AWS access portal](https://docs.aws.amazon.com/signin/latest/userguide/iam-id-center-sign-in-tutorial.html)

* IAM identity
  * == human user OR programmatic workload /
    * is
      * authenticated
      * authorized -- to perform -- actions | AWS
  * 👀EACH IAM identity -- can be associated with -- >= 1 *policies* 👀
* Policies
  * determine
    * what actions a user, role, or member of a user group can perform
    * | which 
      * AWS resources
      * conditions

## [AWS account root user](id_root-user.md)<a name="id_root"></a>

* identity / create the AWS account
  * complete access | AWS account, to ALL
    * AWS services
    * resources
  * requirements
    * email address
    * password
  * can create *IAM identities* / -- provides access to an -- AWS account

* recommendations
  * NOT use -- for -- everyday tasks
* [Tasks / require root user credentials](https://docs.aws.amazon.com/accounts/latest/reference/root-user-tasks.html)

## [IAM users](id_users.md)<a name="id_iam-users"></a>

* == identity | your AWS account / 
  * 👀has specific permissions -- for a -- 1! person or application👀
  * [how to create an IAM user | your AWS account](id_users_create.md)
  * recommendations
    * see [best practices](best-practices.md)
    * 👀temporary credentials better than IAM users / have long-term credentials (_Example:_ passwords and access keys)👀
    * if you have specific use cases / require long-term credentials -- via -- IAM users -> rotate access keys
      * see [Rotate access keys](best-practices.md#rotate-credentials)

## [IAM user groups](id_groups.md)<a name="id_iam-groups"></a>

* == collection of IAM users /-- managed as a -- unit
  * uses
    * ❌NOT to sign-in ❌
    * specify permissions | MULTIPLE users | time
      * -> easier to manage permissions | large set of users
* see [IAM User Groups](id_groups.md)

## [IAM roles](id_roles.md)<a name="id_iam-roles"></a>

* == identity | your AWS account /
  * has specific permissions
  * vs IAM user
    * ❌-- NOT associated with a -- specific person❌
  * ways to assume a role
    * calling an operation of 
      * AWS CLI
      * AWS API
    * using a custom URL
    * temporarily | AWS Management Console -- via -- [switching roles](#when-to-create-an-iam-role-instead-of-a-usera-nameid_which-to-choose_rolea)
    * see [Using IAM roles](id_roles_use.md)

* use cases
  * IAM roles / temporary credentials
    + **Federated user access**
      + steps
        + create a role
        + define permissions / role
      + see 
        + [Federated scenarios](id_roles_common-scenarios_federated-users.md)
        + [Creating a role | TP Identity Provider](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-idp.html)
        + [ Permission sets](https://docs.aws.amazon.com/singlesignon/latest/userguide/permissionsetsconcept.html)
    + **Temporary IAM user permissions**
      + uses
        + take on different permissions / specific task
    + **Cross\-account access**
      + TODO:– You can use an IAM role to allow someone \(a trusted principal\) in a different account to access resources in your account\. 
      + Roles are the primary way to grant cross\-account access\. 
      + However, with some AWS services, you can attach a policy directly to a resource \(instead of using a role as a proxy\)\. 
      + To learn the difference between roles and resource\-based policies for cross\-account access, see [How IAM roles differ from resource\-based policies](id_roles_compare-resource-policies.md)\.
    + **Cross\-service access** –  Some AWS services use features in other AWS services\. For example, when you make a call in a service, it's common for that service to run applications in Amazon EC2 or store objects in Amazon S3\. A service might do this using the calling principal's permissions, using a service role, or using a service\-linked role\. 
      + **Principal permissions** –  When you use an IAM user or role to perform actions in AWS, you are considered a principal\. Policies grant permissions to a principal\. When you use some services, you might perform an action that then triggers another action in a different service\. In this case, you must have permissions to perform both actions\. To see whether an action requires additional dependent actions in a policy, see [Actions, resources, and condition keys for AWS Identity and Access Management](https://docs.aws.amazon.com/service-authorization/latest/reference/list_identityandaccessmanagement.html) in the *Service Authorization Reference*\. 
      + **Service role** –  A service role is an [IAM role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) that a service assumes to perform actions on your behalf\. An IAM administrator can create, modify, and delete a service role from within IAM\. For more information, see [Creating a role to delegate permissions to an AWS service](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-service.html) in the *IAM User Guide*\. 
      + **Service\-linked role** –  A service\-linked role is a type of service role that is linked to an AWS service\. The service can assume the role to perform an action on your behalf\. Service\-linked roles appear in your AWS account and are owned by the service\. An IAM administrator can view, but not edit the permissions for service\-linked roles\. 
    + **Applications running on Amazon EC2** –  You can use an IAM role to manage temporary credentials for applications that are running on an EC2 instance and making AWS CLI or AWS API requests\. This is preferable to storing access keys within the EC2 instance\. To assign an AWS role to an EC2 instance and make it available to all of its applications, you create an instance profile that is attached to the instance\. An instance profile contains the role and enables programs that are running on the EC2 instance to get temporary credentials\. For more information, see [Using an IAM role to grant permissions to applications running on Amazon EC2 instances](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use_switch-role-ec2.html) in the *IAM User Guide*\. 

* see *[IAM role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html)*

## [Temporary credentials | IAM](id_credentials_temp.md)<a name="id_temp-creds"></a>

As a [best practice](best-practices.md), use temporary credentials with both human users and workloads\. Temporary credentials are primarily used with IAM roles, but there are also other uses\. You can request temporary credentials that have a more restricted set of permissions than your standard IAM user\. This prevents you from accidentally performing tasks that are not permitted by the more restricted credentials\. A benefit of temporary credentials is that they expire automatically after a set period of time\. You have control over the duration that the credentials are valid\.

## When to use IAM Identity Center users?<a name="id_sso_users"></a>

 We recommend that all human users use IAM Identity Center to access AWS resources\. IAM Identity Center enables significant improvements over accessing AWS resources as an IAM user\. IAM Identity Center provides:
+ A central set of identities and assignments
+ Access to accounts across an entire AWS Organization 
+ Connection to your existing identity provider
+ Temporary credentials
+ Multi\-factor authentication \(MFA\) 
+ Self\-service MFA configuration for end\-users
+ Administrative enforcement of MFA usage
+ Single sign\-on to all AWS account entitlements

* see [What is IAM Identity Center](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)
  * successor to AWS Single Sign-On

## When to create an IAM user \(instead of a role\)<a name="id_which-to-choose"></a>

We recommend you only use IAM users for use cases not supported by federated users\. Some of the use cases include the following:
+ **Workloads that cannot use IAM roles** – You might run a workload from a location that needs to access AWS\. In some situations, you can't use IAM roles to provide temporary credentials, such as for WordPress plugins\. In these situations, use IAM user long\-term access keys for that workload to authenticate to AWS\.
+ **Third\-party AWS clients** – If you are using tools that don’t support access with IAM Identity Center, such as third\-party AWS clients or vendors that are not hosted on AWS, use IAM user long\-term access keys\.
+ **AWS CodeCommit access** – If you are using CodeCommit to store your code, you can use an IAM user with either SSH keys or service\-specific credentials for CodeCommit to authenticate to your repositories\. We recommend that you do this in addition to using a user in IAM Identity Center for normal authentication\. Users in IAM Identity Center are the people in your workforce who need access to your AWS accounts or to your cloud applications\. To give users access to your CodeCommit repositories without configuring IAM users, you can configure the git\-remote\-codecommit utility\. For more information about IAM and CodeCommit, see [Using IAM with CodeCommit: Git credentials, SSH keys, and AWS access keys](id_credentials_ssh-keys.md)\. For more information about configuring the git\-remote\-codecommit utility, see [Connecting to AWS CodeCommit repositories with rotating credentials](https://docs.aws.amazon.com/codecommit/latest/userguide/temporary-access.html#temporary-access-configure-credentials) in the *AWS CodeCommit User Guide*\.
+ **Amazon Keyspaces \(for Apache Cassandra\) access** – In a situation where you are unable to use users in IAM Identity Center, such as for testing purposes for Cassandra compatibility, you can use an IAM user with service\-specific credentials to authenticate with Amazon Keyspaces\. Users in IAM Identity Center are the people in your workforce who need access to your AWS accounts or to your cloud applications\. You can also connect to Amazon Keyspaces using temporary credentials\. For more information, see [Using temporary credentials to connect to Amazon Keyspaces using an IAM role and the SigV4 plugin](https://docs.aws.amazon.com/keyspaces/latest/devguide/access.credentials.html#temporary.credentials.IAM) in the *Amazon Keyspaces \(for Apache Cassandra\) Developer Guide*\.
+ **Emergency access** – In a situation where you cannot access your identity provider and you must take action in your AWS account\. Establishing emergency access IAM users can be part of your resiliency plan\. We recommend that the emergency user credentials be tightly controlled and secured using multi\-factor authentication \(MFA\)\.

## When to create an IAM role \(instead of a user\)<a name="id_which-to-choose_role"></a>

Create an IAM role in the following situations:

**You're creating an application that runs on an Amazon Elastic Compute Cloud \(Amazon EC2\) instance and that application makes requests to AWS\.**  
Don't create an IAM user and pass the user's credentials to the application or embed the credentials in the application\. Instead, create an IAM role that you attach to the EC2 instance to give temporary security credentials to applications running on the instance\. When an application uses these credentials in AWS, it can perform all of the operations that are allowed by the policies attached to the role\. For details, see [Using an IAM role to grant permissions to applications running on Amazon EC2 instances](id_roles_use_switch-role-ec2.md)\.

**You're creating an app that runs on a mobile phone and that makes requests to AWS\.**  
Don't create an IAM user and distribute the user's access key with the app\. Instead, use an identity provider like Login with Amazon, Amazon Cognito, Facebook, or Google to authenticate users and map the users to an IAM role\. The app can use the role to get temporary security credentials that have the permissions specified by the policies attached to the role\. For more information, see the following:   
+ [Amazon Cognito User Guide](https://docs.aws.amazon.com/cognito/latest/developerguide/cognito-identity.html)
+ [About web identity federation](id_roles_providers_oidc.md)

**Users in your company are authenticated in your corporate network and want to be able to use AWS without having to sign in again—that is, you want to allow users to federate into AWS\.**  
Don't create IAM users\. Configure a federation relationship between your enterprise identity system and AWS\. You can do this in two ways:   
+ If your company's identity system is compatible with SAML 2\.0, you can establish trust between your company's identity system and AWS\. For more information, see [About SAML 2\.0\-based federation](id_roles_providers_saml.md)\.
+ Create and use a custom proxy server that translates user identities from the enterprise into IAM roles that provide temporary AWS security credentials\. For more information, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\.