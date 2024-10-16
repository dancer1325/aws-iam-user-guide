## Regions and endpoints<a name="id_credentials_region-endpoints"></a>

* endpoints / Regions
  * some are activated by default
  * some can be activated or deactivated
  * [check the table](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_temp_region-endpoints.html)
    * ¹ if you want to use it -> you must [enable the Region](https://docs.aws.amazon.com/general/latest/gr/rande-manage.html) ->
      * automatically activates AWS STS
      * can NOT manually | these Regions
        * activate AWS STS 
        * deactivate AWS STS
    * ² if you want to use AWS | China -> needed an account and credentials specific to AWS | China

## AWS CloudTrail and Regional endpoints<a name="sts-regions-cloudtrail"></a>

* if you calls to
  * Regional endpoints (_Example:_ `us-east-2.amazonaws.com`) ->  logged | AWS CloudTrail
    * == call to a Regional service
  * global endpoint, `sts.amazonaws.com` -> logged == calls to a global service
* [Logging IAM and AWS STS API calls with AWS CloudTrail](cloudtrail-integration.md)