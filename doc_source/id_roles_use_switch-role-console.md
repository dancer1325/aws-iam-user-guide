# Switching to a role \(console\)<a name="id_roles_use_switch-role-console"></a>


* IAM roles / switched,
  * can be |
    * your own AWS account or
    * any other AWS account
  * 👀the role's permissions are NOT cumulative 👀
    * = ONLY 1 set of permissions is active | time
  * how does it work?
    * authorize the switch -- via -- your original credentials /
      * check if you -- are allowed to assume the -- new role
    * you temporarily give up your user permissions
    * work with the other permissions / -- assigned to the -- changed role
    * 👀if you exit the role -> your user permissions are automatically restored 👀
  * requirements
    * sign in -- as an --
      * IAM user,
      * user | IAM Identity Center,
      * SAML\-federated role,
      * web-identity federated role 
    * if role requires an [ExternalId](id_roles_create_for-user_externalid.md) value -> call the [API AssumeRole](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) / supports the `ExternalId` parameter
 
## Extra information about switching roles | console<a name="id_roles_iam_user-switch-role-console-things-to-know"></a>

* AWS Management Console session
  * by default, 1 hour
    * vs IAM user sessions = 12 hours, by default
  * way to determine the switch role session duration
    
    | IAM user session time remaining is… | Role session duration is… | 
    | --- | --- | 
    | < role maximum session duration | Time remaining in user session | 
    | \> role maximum session duration | Maximum session duration value | 
    | == role maximum session duration | Maximum session duration value \(approximate\) | 

  * SOME AWS service consoles -- can autorenew, WITHOUT any action, your -- role session | it expires

* steps -- to switch to a -- role | AWS console
  1. Sign in | AWS Management Console -- as an -- allowed one to switch
  2. | IAM console, choose your user name | navigation bar | upper right
  3. Choose **Switch Role**
     1. The last several roles / you used -> appear | menu
  4. | the **Switch Role** page, type the 
     1. account ID number or account alias
     2. complete path + name of the role / -- provided by your -- administrator
        1. _Example:_ `division_abc/subdivision_efg/roleToDoX`
        2. if you type ONLY the role name, OR `Path` + `RoleName`'s length > 64 characters -> the role switch fails
     3. -> looks like ***rolename*@*account\_ID\_number\_or\_alias*** 
  5. Choose a **Display name** & color to highlight it
     1. type text / would appear | navigation bar, instead of your user name | this role is active
        1. name is suggested -- based on the -- account & role information
     2. 💡the administrator can create a link / go directly to this step 💡
        1. link format / `text_to_display` is optional
          ```
          https://signin.aws.amazon.com/switchrole?account=account_id_numberOralias&roleName=role_name&displayName=text_to_display 
          ```
      
  6. Choose **Switch Role**
     1. -> display name & color -- replace your -- user name | navigation bar

  _Example:_ 
    * you are signed | account number `123456789012` -- via -- user name `RichardRoe`
    * you switch to `AdminRole` role

      ![\[Richard Roe stops using the AdminRole role\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/role-stop-using.png)

* steps -- to stop using a -- role | console
  1. | IAM console, choose your role's **Display name** | navigation bar | upper right
  2. Choose **Back to *username***
     1. -> 
        1. role & its permissions are deactivated
        2. permissions / associated with your IAM user & groups -- are automatically -- restored
 