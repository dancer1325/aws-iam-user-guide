# Identity\-based policies & resource\-based policies<a name="access_policies_identity-vs-resource"></a>

* policy
  * == AWS' object /
    * if it's -- associated with an -- identity OR resource -> defines their permissions
* permissions policy
  * if you want to restrict access to a resource -> choose between
    * *identity\-based policy*
      * are attached | IAM
        * user,
        * group,
        * role
      * allows
        * specifying what that identity can do 
          * == its permissions
      * can be [managed or inline](access_policies_managed-vs-inline.md) 
    * *resource-based policy*
      * are attached | resource
        * see [AWS services / support resource-based policies](reference_aws-services-that-work-with-iam.md)
      * allows
        * specifying
          * who -- has access to the -- resource
          * what actions can perform | it
      * ONLY inline
        * NOT managed
      * if you want to know whether principals | accounts outside of your zone of trust, have access -> see [What is IAM Access Analyzer?](what-is-access-analyzer.md)
      * 👀!= *resource-level* permissions👀
        * specify individual resources | policy, -- via -- [ARNs](reference_identifiers.md#identifiers-arns)
        * see [AWS services / support resource-level permissions](reference_aws-services-that-work-with-iam.md)
  * identity-based policies -- interact with -- resource-based policies | SAME account
    * see [Evaluating policies within a single account](reference_policies_evaluation-logic.md#policy-eval-basics)
  * 👀/ -- interact across -- accounts 👀
    * see [Cross\-account policy evaluation logic](reference_policies_evaluation-logic-cross-account.md)
  * are evaluated together (identity-based & resource-based)
    * see [policy evaluation logic](reference_policies_evaluation-logic.md)
* _Example:_ 
  * identity-based policies
    * *resource\-level permission* | identity\-based policy
      * == actions -- can be -- performed | specific resources
        * _Example:_ user `JohnSmith` can perform some actions | `Resource X`
  * resource-based policies
    * _Example:_ | `Resource X`, `Resource Y`, and `Resource Z`

  ![\[Identity-based vs resource-based policies\]](http://docs.aws.amazon.com/IAM/latest/UserGuide/images/Types_of_Permissions.diagram.png)

  * allowed listed actions / user
    + **JohnSmith**
      + list, read actions | `Resource X` 
    + **CarlosSalazar**
      + list, read, and write actions | `Resource Y`
      + NO actions | `Resource Z` 
    + **MaryMajor**
      + list, read, and write operations | `Resource X`, `Resource Y`, and `Resource Z`
    + **ZhangWei**
      + FULL access | `Resource Z
      + list and read actions | `Resource Y`
