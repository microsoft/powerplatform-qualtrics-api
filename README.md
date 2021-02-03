# Sample integration for [Qualtrics  Surveys](https://www.qualtrics.com/) &reg into [Microsoft Power Platform](https://make.powerapps.com)

> This repository contains sample code to demonstrate integration of Qualtrics $reg survey data and survey events into Microsoft Power Platform.
> The OpenAPI 2.0 compliant SWAGGER file can be used as the base to create a Microsoft Power Platform custom connector. 

The sample code implements the following actions on the Qualtrics &reg API located at [https://api.qualtrics.com/](https://api.qualtrics.com/)
To gain access to the API a Qualtrics account is required.

**Triggers**

* When a survey response is submitted (see caution note below)

  Triggers when a response is submitted to a survey. Takes the SurveyID (e.g: SV_123) in the topic field to subscribe to the right survey events. 

**Actions**

* Create contact in mailing list

  POST new contact data to a given Qualtrics directory and mailing list.
DirectoryId and MailingListId can be obtained from the Qualtrics API portal.
    
* Get distributions for survey
  
  Get distributions for a given survey
  
* Generate distribution links
  
  Generate individual links for a given distribution

* Retrieve distribution links

  Retrieve the links generated with Generate distribution links action
  
* Get event subscriptions
  
  Get all the registered events. Will return all the events that are registered with a webhook endpoint. See the [Qualtrics API documentation](https://api.qualtrics.com/api-reference/reference/eventSubscriptions.json/paths/~1eventsubscriptions/post) for a list of topics that can be subscribed.
  
* Get survey

  Returns a given survey
  
* Remove event subscription (see note below)

  Dummy
 
**Caution with the trigger**

The trigger definition (When a survey response is submitted) registers a webhook endpoint in the Qualtrics API. Microsoft mandates that any trigger that creates a webhook includes a location header to indicate to Power Platform how to de-register the trigger. The LOCATION header points to a DELETE action. As of the time of the publication of this file the Qualtrics API **does not provide a DELETE endpoint**. The DELETE action (Remove event subscription) is only a dummy to make the specification work in PowerPlatform.
This means that any registered webhook endpoint will continue to receive data until the respective survey is deleted.

# Below figure shows the fully imported API specification in action in Microsoft Power Automate

## Contributing

This project welcomes contributions and suggestions.  Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
