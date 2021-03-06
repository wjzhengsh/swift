---

copyright:
  years: 2018
lastupdated: "2018-02-15"

---
{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Developing serverless apps

To facilitate serverless development, IBM's Functions as a Service (FaaS) offering, {{site.data.keyword.openwhisk}}, enables application logic to be run in response to events or direct invocations from web or mobile apps over HTTP without provisioning or managing servers.

Because {{site.data.keyword.openwhisk}} performs the system administration including auto-scaling, availability management, and maintenance, developers can focus on writing application logic.

You can use the browser or the CLI to develop your {{site.data.keyword.openwhisk_short}} applications. Both have similar capabilities for developing applications. The CLI provides more control over your deployment and operations.

For additional information on {{site.data.keyword.openwhisk}}, check out our full [documentation](/docs/openwhisk/index.html).

## {{site.data.keyword.openwhisk_short}} UI

Try out {{site.data.keyword.openwhisk_short}} in your [browser](https://console.{DomainName}/openwhisk/actions). Go to the [Concepts](https://console.{DomainName}/openwhisk/learn) page for a quick tour of the {{site.data.keyword.openwhisk_short}} User Interface.

## Developing with the CLI
{: #openwhisk_start_configure_cli}

To find out more about developing from our {{site.data.keyword.openwhisk_short}} command line interface, see our [Configure CLI documentation](https://console.{DomainName}/openwhisk/cli) and follow the instructions to install it.

## Hello World example

To get started with {{site.data.keyword.openwhisk_short}} from the browser head to {{site.data.keyword.openwhisk_short}} from the developer console.

1. Select **start creating**.
2. Select **create action** and then fill in the form fields. You can namespace your functions as part of a package by creating one and using the drop down to set it.
3. Copy the following code snippet into the editor.

```Swift
/**
 * Hello world as an IBM Functions action.
 */
 func main(args: [String: Any]) -> [String: Any] {
     let name = args["name"] as? String ?? "World"
     return ["payload":  "Hello " + name + "!"]
 }
```
{: codeblock}

4. To set the input parameters, select **change input**.
5.Click **invoke** and you can see the output within the activation sidebar.

For more complex usage examples, including exposing web actions, creating triggers, and building function sequences, check out some of our [tutorials](/docs/tutorials/serverless-mobile-backend.html#mobile-application-with-a-serverless-backend) that will walk you through production level serverless mobile development.

## Exposing APIs and data sets as web actions

By default, {{site.data.keyword.openwhisk_short}} defines actions that require an authentication key. However, in production mobile environments, it is often necessary to authorize mobile clients based on OAuth flows to expose APIs and specific data sets.

{{site.data.keyword.openwhisk_short}} enables developers to expose their functions as web actions, which are annotated, to quickly build web-based applications. These annotated actions enable you to program backend logic that your web application can access anonymously, without requiring an OpenWhisk authentication key.

To expose an action as web actions, navigate to the **endpoints** tab of your action and select **Enable as Web Action**.

Now, users can reach the action from a browser or curl request.

```
$ curl https://openwhisk.ng.bluemix.net/api/v1/web/aaron.m.liberatore_dev/MyPackage/helloWorld.json?name=aaron

{
    message: "Hello aaron!"
}
```

### SDK
{{site.data.keyword.openwhisk_short}} provides a [mobile SDK](..openwhisk/openwhisk_mobile_sdk.html#mobile-sdk) for iOS and watchOS devices that enables mobile apps to easily fire remote triggers and invoke remote actions.

### API Reference
* [REST API Documentation](/docs/openwhisk/openwhisk_reference.html#openwhisk_ref_restapi)
* [REST API](https://console.{DomainName}/apidocs/98)
* [Cloud Funcstions Swift SDK](https://console.bluemix.net/docs/openwhisk/openwhisk_mobile_sdk.html#mobile-sdk)

### Related Links
* [Discover: {{site.data.keyword.openwhisk_short}}](http://www.ibm.com/cloud-computing/bluemix/openwhisk/)
* [{{site.data.keyword.openwhisk_short}} on IBM developerWorks](https://developer.ibm.com/openwhisk/)
* [Apache {{site.data.keyword.openwhisk_short}} project website](http://openwhisk.org)
