# IAM JSON policy elements: Version<a name="reference_policies_elements_version"></a>

* ⚠️!= *policy version* ⚠️
  * policy version
    * uses
      * track changes of a customer managed policy
        * new version / change == NOT overwrite the existing policy
    * see [Versioning IAM policies](access_policies_managed-versioning.md) 
* == version of the policy language
  * == language syntax rules / -- used to -- process a policy
  * supported
    * `2012-10-17`
      * current version of the policy language
      * recommendations
        * use this one
        * 👀if you set (since top-level elements are optional) -> you can use ALL features 👀
          * _Example:_ [policy variables](reference_policies_variables.md)
      * _Example:_ 
        ```
        {
          "Version": "2012-10-17",
          "Statement": [
            {
              "Effect": "Allow",
              "Action": "s3:ListAllMyBuckets",
              "Resource": "*"
            }
          ]
        }
        ``` 
    * `2008-10-17`
      * earlier version
      * recommendations
        * NOT use it
          * Reason: 🧠NEWER features are NOT available 🧠
