# IAM JSON policy elements reference<a name="reference_policies_elements"></a>

* JSON policy documents
  * == elements / listed here | general order
    * 👀order of the elements does NOT matter 👀
    * 👀SOME elements are mutually exclusive | SAME statement👀
      * _Example1:_ `Action`/`NotAction`
      * _Example2:_ `Principal`/`NotPrincipal`
      * _Example3:_ `Resource`/`NotResource`
  * see [Overview of JSON policies](access_policies.md#overview-of-json-policiesa-nameaccess_policies-jsona)
  * 's content -- depend on --
    * service,
    * actions / service makes available,
    * types of resources / service contains
  * see [AWS services / work with IAM](reference_aws-services-that-work-with-iam.md)
  * | create or edit a JSON policy,
    * IAM can perform policy validation / identify JSON syntax errors
      * see [Validating IAM policies](access_policies_policy-validator.md) 
    * IAM Access Analyzer -- provides -- additional policy checks / make recommendations
      * see [ IAM Access Analyzer policy validation](https://docs.aws.amazon.com/IAM/latest/UserGuide/access-analyzer-policy-validation.html) 

**Topics**
+ [Version](reference_policies_elements_version.md)
+ [Id](reference_policies_elements_id.md)
+ [Statement](reference_policies_elements_statement.md)
+ [Sid](reference_policies_elements_sid.md)
+ [Effect](reference_policies_elements_effect.md)
+ [Principal](reference_policies_elements_principal.md)
+ [NotPrincipal](reference_policies_elements_notprincipal.md)
+ [Action](reference_policies_elements_action.md)
+ [NotAction](reference_policies_elements_notaction.md)
+ [Resource](reference_policies_elements_resource.md)
+ [NotResource](reference_policies_elements_notresource.md)
+ [Condition](reference_policies_elements_condition.md)
+ [Variables and tags](reference_policies_variables.md)
+ [Supported data types](reference_policies_elements_datatypes.md)