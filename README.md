
# Bridge to Kubernetes

Welcome to Bridge-To-Kubernetes! Bridge to Kubernetes extends the Kubernetes perimeter to your development computer allowing you to write, test, and debug microservice code while connected to your Kubernetes cluster with the rest of your application or services. You can simply run your code natively on your development workstation while connected to the Kubernetes cluster, allowing you to test your code changes in the context of the larger application.

## Introduction Video
https://learn.microsoft.com/en-us/shows/open-at-microsoft/get-started-with-bridge-to-kubernetes

![image002](https://github.com/Azure/Bridge-To-Kubernetes/assets/105889062/7d71f41d-dafe-4039-afb1-31600f4a793f)

## Key Features:

## Documentation
- [Overview](https://learn.microsoft.com/visualstudio/bridge/overview-bridge-to-kubernetes)
- [Visual Studio](https://learn.microsoft.com/visualstudio/bridge/bridge-to-kubernetes-vs)
- [Visual Studio Code](https://learn.microsoft.com/visualstudio/bridge/bridge-to-kubernetes-vs-code)

## CLI tool installation

Unzip to the location of choice. An example could be c:\users\<username>\.bridge-cli

### Setting up Environment Variables
Two variables are needed to be configured for things to work smoothly. 

- The first is the path variable needs to be updated to include the directory where the bridge-cli files were unzipped too. 
- The next variable that needs to be added is KUBECTL_PROXY.
    - Variable Name = KUBECTL_PROXY
    - Variable Value = http://127.0.0.1:8001



## How to use the CLI

To bridge a service you now need to begin by running the Kubernetes proxy service. To do this run the command. This window will need to remain open whilst bridging.

```kubectl proxy```

Then open up another terminal window (making sure the IDE you are using isn't currently open, if you have already bridged and opened up the IDE and want to bridge another service you don't need to close the IDE) run this command.

```dsc connect --service <service-name> --local-port <port> --namespace <namespace>```

When asked “Once your cluster environment is replicated, all processes on your machine will be able to access it. Do you want to process? (y/N)”, press “y” and return.

This will open a new command prompt, which will eventually return to a prompt.

### Open the IDE to debug
From the command prompt that was opened during the previous step, open your preferred IDE, such as Visual Studio or Rider.

Tip: you may want to add the folder to your preferred IDE to your Path environment variable, following the steps above

### Open the solution and debug
Now you are in your IDE, open the solution you wish to debug. Then you can press the normal button in the toolbar to begin debugging, e.g. 

### General usage
At this point, you can stop debugging, make code changes, debug, and continue the cycle as normal.

### Terminating the bridge-cli
- Stop debugging in the IDE if you are currently doing so
- Close the IDE
- From the command prompt used to open the IDE, type exit and press return
- This command prompt should disappear and the original terminal the bridge command was executed from should return to a prompt
- Kubernetes should now restore the replaced pod into your cluster
- Close the Kubectl Proxy service


## Trademarks
This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft trademarks or logos is subject to and must follow [Microsoft’s Trademark & Brand Guidelines] (https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks). Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship. Any use of third-party trademarks or logos are subject to those third-party’s policies.
 
## Security Reporting Guidance
Checkout the SECURITY.md file in this repo for details.

## Data Collection
The software may collect information about you and your use of the software and send it to Microsoft. Microsoft may use this information to provide services and improve our products and services. You may turn off the telemetry as described in the repository. There are also some features in the software that may enable you and Microsoft to collect data from users of your applications. If you use these features, you must comply with applicable law, including providing appropriate notices to users of your applications together with a copy of Microsoft’s privacy statement. Our privacy statement is located at https://go.microsoft.com/fwlink/?LinkID=824704. You can learn more about data collection and use in the help documentation and our privacy statement. Your use of the software operates as your consent to these practices.

