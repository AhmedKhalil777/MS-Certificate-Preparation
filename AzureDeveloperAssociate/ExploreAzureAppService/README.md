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
