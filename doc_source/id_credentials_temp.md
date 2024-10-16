# Temporary security credentials in IAM<a name="id_credentials_temp"></a>

* temporary security credentials
  * 👁️-- can be created by -- AWS STS👁️
  * uses
    * for trusted users -- to control access to -- AWS resources
  * vs long-term access key credentials
    * work ALMOST identical, except to
      * once the temporary credentials expire -> AWS NO longer recognizes them or allows any kind of access
        * Reason: 🧠temporary == short-lifetime [few minutes, several hours) 🧠
      * temporary security credentials are NOT stored with the user
        * if the user request them -> they are generated dynamically and provided to the user
      *  When or before the temporary security credentials expire -> the user can request new credentials
        * if the user has still permissions -> can request them
    * NO need to
      * distribute or embed | an application
      * define an AWS identity / AWS resources
        * Reason: 🧠temporary credentials -- are based on -- [roles and identity federation](id_roles.md) 🧠
      * rotate them or explicitly revoke them | they're no longer needed
        * Reason: 🧠temporary credentials have short lifetime 🧠

## AWS STS and AWS regions<a name="sts-regionalization"></a>

* AWS STS's enpoints
  * by default, it's a global service / 1! endpoint at `https://sts.amazonaws.com`
  * possible to make endpoints | ANY OTHER supported Region
    * [Managing AWS STS in an AWS Region](id_credentials_temp_enable-regions.md)\

## Common scenarios for temporary credentials<a name="sts-introduction"></a>

* use cases of temporary credentials
  * scenarios / involve
    * identity federation
    * delegation
    * cross\-account access
    * IAM roles

### Identity federation<a name="id-federation"></a>

* TODO:
You can manage your user identities in an external system outside of AWS and grant users who sign in from those systems access to perform AWS tasks and access your AWS resources\. IAM supports two types of identity federation\. In both cases, the identities are stored outside of AWS\. The distinction is where the external system resides—in your data center or an external third party on the web\. For more information about external identity providers, see [Identity providers and federation](id_roles_providers.md)\.
+ **Enterprise identity federation** – You can authenticate users in your organization's network, and then provide those users access to AWS without creating new AWS identities for them and requiring them to sign in with different sign\-in credentials\. This is known as the *single sign\-on* approach to temporary access\. AWS STS supports open standards like Security Assertion Markup Language \(SAML\) 2\.0, with which you can use Microsoft AD FS to leverage your Microsoft Active Directory\. You can also use SAML 2\.0 to manage your own solution for federating user identities\. For more information, see [About SAML 2\.0\-based federation](id_roles_providers_saml.md)\.
  + **Custom federation broker** – You can use your organization's authentication system to grant access to AWS resources\. For an example scenario, see [Enabling custom identity broker access to the AWS console](id_roles_providers_enable-console-custom-url.md)\.
  + **Federation using SAML 2\.0** – You can use your organization's authentication system and SAML to grant access to AWS resources\. For more information and an example scenario, see [About SAML 2\.0\-based federation](id_roles_providers_saml.md)\.
+ **Web identity federation** – You can let users sign in using a well\-known third\-party identity provider such as Login with Amazon, Facebook, Google, or any OpenID Connect \(OIDC\) 2\.0 compatible provider\. You can exchange the credentials from that provider for temporary permissions to use resources in your AWS account\. This is known as the *web identity federation* approach to temporary access\. When you use web identity federation for your mobile or web application, you don't need to create custom sign\-in code or manage your own user identities\. Using web identity federation helps you keep your AWS account secure, because you don't have to distribute long\-term security credentials, such as IAM user access keys, with your application\. For more information, see [About web identity federation](id_roles_providers_oidc.md)\.

   AWS STS web identity federation supports Login with Amazon, Facebook, Google, and any OpenID Connect \(OIDC\)\-compatible identity provider\.
**Note**  
For mobile applications, we recommend that you use Amazon Cognito\. You can use this service with AWS SDKs for mobile development to create unique identities for users and authenticate them for secure access to your AWS resources\. Amazon Cognito supports the same identity providers as AWS STS, and also supports unauthenticated \(guest\) access and lets you migrate user data when a user signs in\. Amazon Cognito also provides API operations for synchronizing user data so that it is preserved as users move between devices\. For more information, see [Authentication with Amplify](https://docs.amplify.aws/lib/auth/getting-started/q/platform/js/#authentication-with-amplify) in the *Amplify Documentation*\.

### Roles for cross\-account access<a name="role_cross-account"></a>

Many organizations maintain more than one AWS account\. Using roles and cross\-account access, you can define user identities in one account, and use those identities to access AWS resources in other accounts that belong to your organization\. This is known as the *delegation* approach to temporary access\. For more information about creating cross\-account roles, see [Creating a role to delegate permissions to an IAM user](id_roles_create_for-user.md)\. To learn whether principals in accounts outside of your zone of trust \(trusted organization or account\) have access to assume your roles, see [What is IAM Access Analyzer?](https://docs.aws.amazon.com/IAM/latest/UserGuide/what-is-access-analyzer.html)\.

### Roles for Amazon EC2<a name="role_ec2"></a>

If you run applications on Amazon EC2 instances and those applications need access to AWS resources, you can provide temporary security credentials to your instances when you launch them\. These temporary security credentials are available to all applications that run on the instance, so you don't need to store any long\-term credentials on the instance\. For more information, see [Using an IAM role to grant permissions to applications running on Amazon EC2 instances](id_roles_use_switch-role-ec2.md)\. 

### Other AWS services<a name="other-services"></a>

* [list of AWS services / accept temporary security credentials](reference_aws-services-that-work-with-iam.md)