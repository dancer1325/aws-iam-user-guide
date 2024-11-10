# IAM JSON policy elements: Sid<a name="reference_policies_elements_sid"></a>

* `Sid`
  * == Statement ID
    * == identifier / EACH statement | statement array
  * optional 
  * uses
    * description for the policy statement 
  * use cases
    * == sub-ID of the policy document ID
      * _Example:_ | SNS or SQS
    * 👀| IAM, 's value MUST be UNIQUE | JSON policy 👀
    * service-specific requirements could have
      * _Example:_ | SQS or SNS
  * supports
    * ASCII uppercase letters \(A\-Z\),
    * lowercase letters \(a\-z\),
    * numbers \(0\-9\) 
  * 👀NOT exposed -- through -- IAM API 👀
    * -> NOT possible to retrieve a statement -- based on -- it
