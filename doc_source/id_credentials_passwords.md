# Managing user passwords | AWS<a name="id_credentials_passwords"></a>

* passwords
  * can be managed by you
  * uses
    * AWS account root user
    * IAM users | your account
      * -- to access the -- AWS Management Console (❌NOT AWS CLI, Tools for Windows PowerShell, the AWS SDKs or APIs❌) 
* [access keys](id_credentials_access-keys.md)
  * uses
    * IAM users -- can access -- 
      * AWS CLI,
      * Tools for Windows PowerShell,
      * AWS SDKs or APIs
  * recommendations
    * use better [alternatives to long-term access keys](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#alternatives-to-long-term-access-keys) 

**Topics**
+ [Changing the AWS account root user password](id_credentials_passwords_change-root.md)
+ [Setting an account password policy for IAM users](id_credentials_passwords_account-policy.md)
+ [Managing passwords for IAM users](id_credentials_passwords_admin-change-user.md)
+ [Permitting IAM users to change their own passwords](id_credentials_passwords_enable-user-change.md)
+ [How an IAM user changes their own password](id_credentials_passwords_user-change-own.md)