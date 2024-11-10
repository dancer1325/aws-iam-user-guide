# IAM JSON policy elements: Statement<a name="reference_policies_elements_statement"></a>

* == MAIN element for a policy
  * 👀required 👀
  * ⚠️== array of individual statements ⚠️
    * array of 1 ! statement, ALSO possible
    * enclosed with
      * `[]` | MULTIPLE statements 
      * `{}` / EACH individual statement block
      ```
      "Statement": [{...},{...},{...}]
      ```
  * _Example:_ array of 3 statements | 1! `Statement` element 
  
    ```
    {
      "Version": "2012-10-17",
      "Statement": [
        {
          "Effect": "Allow",
          "Action": [
            "s3:ListAllMyBuckets",
            "s3:GetBucketLocation"
          ],
          "Resource": "arn:aws:s3:::*"
        },
        {
          "Effect": "Allow",
          "Action": "s3:ListBucket",
          "Resource": "arn:aws:s3:::BUCKET-NAME",
          "Condition": {"StringLike": {"s3:prefix": [
            "",
            "home/",
            "home/${aws:username}/"
          ]}}
        },
        {
          "Effect": "Allow",
          "Action": "s3:*",
          "Resource": [
            "arn:aws:s3:::BUCKET-NAME/home/${aws:username}",
            "arn:aws:s3:::BUCKET-NAME/home/${aws:username}/*"
          ]
        }
      ]
    }
    ```

  * see [Introduction](reference_policies_variables.md#policy-vars-intro)
