# Explore Azure App Service 

---

> Azure App Service is an __HTTP-based__ service for hosting _web applications, REST APIs, and mobile back ends_. You can develop in your favorite programming language, be it .NET, .NET Core, Java, Ruby, Node.js, PHP, or Python. Applications run and scale with ease on both Windows and Linux-based environments.

## Learning Objectives

- Describe Azure App Service key components and value.
- Explain how Azure App Service manages authentication and authorization.
- Identify methods to control inbound and outbound traffic to your web app.
- Deploy an app to App Service using Azure CLI commands.


## Examine Azure App Service

### Built-in auto scale support

- Baked into Azure App Service is the ability to scale _up/down_ or scale _out/in_. 
- Depending on the usage of the web app, you can scale the resources of the underlying machine that is hosting your web app up/down .
- Resources include the number of cores or the amount of RAM available.
- Scaling out/in is the ability to increase, or decrease, the number of machine instances that are running your web app.

### Continuous integration/deployment support

- The Azure portal provides _out-of-the-box_ continuous integration and deployment with Azure DevOps, GitHub, Bitbucket, FTP, or a local Git repository on your development machine.
- Connect your web app with any of the above sources and App Service will do the rest for you by _auto-syncing_ code and any future changes on the code into the web app.

### Deployment slots

- When you deploy your web app, web app on Linux, mobile back end, or API app to Azure App Service, you can use a _separate deployment slot_ instead of the default _production slot_ when you're running in the _Standard, Premium, or Isolated_ App Service plan tier. 
- Deployment slots are live apps with their own host names.
- App content and configurations elements can be _swapped_ between two deployment slots, including the production slot.

### App Service on Linux

- App Service can also host web apps natively on Linux for supported application stacks.
- It can also run custom Linux containers (also known as Web App for Containers).
- App Service on Linux supports a number of language specific built-in images. Just deploy your code. Supported languages include: Node.js, Java (JRE 8 & JRE 11), PHP, Python, .NET Core, and Ruby. If the runtime your application requires is not supported in the built-in images, you can deploy it with a custom container.

> The languages, and their supported versions, are updated on a regular basis. You can retrieve the current list by using the following command in the Cloud Shell.


```ps1
az webapp list-runtimes --linux
```

### Limitations

App Service on Linux does have some limitations:

- App Service on Linux is not supported on Shared pricing tier.
- You can't mix Windows and Linux apps in the same App Service plan.
- Historically, you could not mix Windows and Linux apps in the same resource group. However, all resource groups created on or after January 21, 2021 do support this scenario. Support for resource groups created before January 21, 2021 will be rolled out across Azure regions (including National cloud regions) soon.
- The Azure portal shows only features that currently work for Linux apps. As features are enabled, they're activated on the portal.

## Examine Azure App Service plans

> In App Service, an app (Web Apps, API Apps, or Mobile Apps) always runs in an App Service plan. 
> An App Service plan defines a set of compute resources for a web app to run. One or more apps can be configured to run on the same computing resources (or in the same App Service plan). In addition, Azure Functions also has the option of running in an App Service plan.

![Plan](./Azure%20Service%20Plan%20Compose.drawio.png)

- When you create an App Service plan in a certain region (for example, West Europe), a set of compute resources is created for that plan in that region. 
- Whatever apps you put into this App Service plan run on these compute resources as defined by your App Service plan. Each App Service plan defines:

  - Region (West US, East US, etc.)
  - Number of VM instances
  - Size of VM instances (Small, Medium, Large)
  - Pricing tier (Free, Shared, Basic, Standard, Premium, PremiumV2, PremiumV3, Isolated)

- The pricing tier of an App Service plan determines what App Service features you get and how much you pay for the plan. There are a few categories of pricing tiers:

- __Shared compute__: Both Free and Shared share the resource pools of your apps with the apps of other customers.
  - These tiers allocate CPU quotas to each app that runs on the shared resources
  - the resources can't scale out.
- __Dedicated compute__: The Basic, Standard, Premium, PremiumV2, and PremiumV3 tiers run apps on dedicated Azure VMs. 
  - Only apps in the same App Service plan share the same compute resources. 
  - The higher the tier, the more VM instances are available to you for scale-out.
- Isolated: This tier runs dedicated Azure VMs on dedicated Azure Virtual Networks. It provides network isolation on top of compute isolation to your apps. 
  - It provides the maximum scale-out capabilities.
- Consumption: This tier is only available to function apps.
  - It scales the functions dynamically depending on workload.

> App Service Free and Shared (preview) hosting plans are base tiers that run on the same Azure virtual machines as other App Service apps. Some apps might belong to other customers. These tiers are intended to be used only for development and testing purposes.

### How does my app run and scale?

In the Free and Shared tiers, an app receives CPU minutes on a shared VM instance and can't scale out. In other tiers, an app runs and scales as follows:

- An app runs on all the VM instances configured in the App Service plan.
- If multiple apps are in the same App Service plan, they all share the same VM instances.
- If you have multiple deployment slots for an app, all deployment slots also run on the same VM instances.
- If you enable diagnostic logs, perform backups, or run WebJobs, they also use CPU cycles and memory on these VM instances.

In this way, the App Service plan is the scale unit of the App Service apps. If the plan is configured to run five VM instances, then all apps in the plan run on all five instances. If the plan is configured for autoscaling, then all apps in the plan are scaled out together based on the autoscale setting

### What if my app needs more capabilities or features?

- Your App Service plan can be scaled up and down at any time.
  - It is as simple as changing the pricing tier of the plan. 
- If your app is in the same App Service plan with other apps, you may want to improve the app's performance by isolating the compute resources. 
  - You can do it by moving the app into a separate App Service plan.

You can potentially save money by putting multiple apps into one App Service plan. However, since apps in the same App Service plan all share the same compute resources you need to understand the capacity of the existing App Service plan and the expected load for the new app.

- Isolate your app into a new App Service plan when:
  - The app is resource-intensive.
  - You want to scale the app independently from the other apps in the existing plan.
  - The app needs resource in a different geographical region.

This way you can allocate a new set of resources for your app and gain greater control of your apps.