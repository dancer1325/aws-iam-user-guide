# IAM JSON policy elements: Effect<a name="reference_policies_elements_effect"></a>

* required
* valid values / case sensitive 
  * `Allow`
  * `Deny` 
    * default one
* _Example:_
    ```
    "Effect":"Allow"
    ```
* policy evaluation logic
  * if you want to override an allow -> set `Deny` 
  * see [Policy evaluation logic](reference_policies_evaluation-logic.md)
