# Test
 
I am assuming an Ecom website where all frontend deigns been developing in JS and API is using for Authenticating users in different stages from website signup to placing orders and delivering orders. And Db is using to store all data of different stages on website. And achieving this by dashboard is a web-based Kubernetes user interface. You can use Dashboard to deploy containerised applications to a Kubernetes cluster, troubleshoot your containerised application, and manage the cluster resources. You can use Dashboard to get an overview of applications running on your cluster, as well as for creating or modifying individual Kubernetes resources (such as Deployments, Jobs, DaemonSets, etc).

The application built as a part of this quest is a simple browser based e-com website whose front end is written using Javascript and the operations (Registration, Shopping cart etc) are served by following micro services written in various programming languages:
The ORMAE and login services are rest api based implementations not doing much tangibly but only serve basic frontend UI functions as APIs. The ORMAE Db acts as a backend service that stores and retrieves data provided to it via the UI API.
The frontend application designed in js. It resembles a calculator, two of whose primary operations i.e. Add and Subtract are served by the expressed service and the other two operations, i.e. multiply and division are served by the happy service.
Along with the micro-services, following components are deployed in the cluster as well:
1. API Gateway  - Ambassador is an open source Kubernetes-Native API Gateway built on the Envoy Proxy which is a native kubernetes api gateway.
2. Redis (data store) -  Redis acted as a data store for this implementation, storing the operations done on the calculator and serving them on on demand. 
The Authentication API enables you to manage all aspects of user identity when you use Auth0. It offers endpoints so your users can log in, sign up, log out, access APIs, and more.

Architecture
The complete architecture of this implementation can be summarised as:
As we can see, Ambassador API is acting as a single point of entry in the Kubernetes cluster, channeling all the incoming requests (Signups, Sign-in’s, new order places etc) to appropriate services. The various microservices are deployed at the following addresses inside the cluster:


Each one of the microservices has liveness and readiness probes inbuilt for the cluster to determine their health and update the users about any potential downtime. The probes are configured for each service at the endpoints:

All the services are currently deployed under the default namespace to keep things simple. However we strongly suggest that users should opt for different namespaces specially if they are planning to deploy their DEV, QA and UAT environments all on the same cluster (of course assuming PROD is going to be an independent cluster)




