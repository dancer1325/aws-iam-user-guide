# IAM JSON policy elements: Action<a name="reference_policies_elements_action"></a>

* `Action`
  * := element / describes the specific action or actionS / -- will be -- allowed or denied
  * Statements -- must include -- 
    * `Action` element or
    * `NotAction` element
  * specific / EACH AWS service
    * _Example:_
      * [allowed Actions | S3](https://docs.aws.amazon.com/AmazonS3/latest/dev/using-with-s3-actions.html)
      * [allowed Actions | EC2](https://docs.aws.amazon.com/AWSEC2/latest/APIReference/query-apis.html)
      * [allowed Actions | IAM](https://docs.aws.amazon.com/IAM/latest/APIReference/API_Operations.html)
  * = `serviceNamespace:actionNameSupportedByTheService`
    * syntax of the value
    * `serviceNamespace` & `actionNameSupportedByTheService` are case insensitive 
      * _Example:_ `iam:ListAccessKeys` == `IAM:listaccesskeys`
    * _Example:_ 
    
      ```
        "Action": "sqs:SendMessage"
      ```

      ```
      "Action": "ec2:StartInstances"
      ```

      ```
      "Action": "iam:ChangePassword"
      ```

      ```
      "Action": "s3:GetObject"
      ```

      ```
      # Specifying several
      
      "Action": [ "sqs:SendMessage", "sqs:ReceiveMessage", "ec2:StartInstances", "iam:ChangePassword", "s3:GetObject" ]
      ```

      ```
      # *         ==          / ALL the AWS actions

      "Action": "s3:*"
      ```

      ```
      # *         for pattern action name    

      "Action": "iam:*AccessKey*"
      ```

    * SOME services let limit more the actions
      * _Example:_ [SQS](https://docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/acp-overview.html#PermissionTypes)