# Integrate Events from AWS IoT SiteWise with SAP S/4HANA using SAP BTP
 
 [![REUSE status](https://api.reuse.software/badge/github.com/SAP-samples/btp-events-to-business-actions-framework)](https://api.reuse.software/info/github.com/SAP-samples/btp-events-to-business-actions-framework)
 
 This repository contains code samples and instructions for developing an extension application in SAP BTP. The sample application has been developed in a partner collaboration to help customers integrate any type of events from systems into SAP ecosystem via SAP BTP. This application helps to configure actions that needs to be taken in SAP LoB systems based on the events that is received in SAP Advanced Event Mesh. The application scenario you will develop in this tutorial leverages Event-To-Business actions framework (extension application).
 
 This framework can be used in combination with any hyperscalar/telco IoT.
 
 In this tutorial, the **events** are received from **AWS IoT SiteWise** and the **actions** for these events are taken in **SAP S/4HANA**. You can use this application to further customize it for other systems as well.
 
 
 ## Scenario
 
**AWS IoT SiteWise** is a managed service with which you can collect, store, organize and monitor data from industrial equipment at scale to help you make better, data-driven decisions. You can use AWS IoT SiteWise to monitor operations across facilities, quickly compute common industrial performance metrics, and create applications that analyze industrial equipment data to prevent costly equipment issues and reduce gaps in production.

However, the events only provides valuable results if any business action is taken on them. To reduce the burden of change management and ensure action is taken on the AWS IoT SiteWise events, this sample project has demonstrated how to automatically record the AWS IoT SiteWise inferences in SAP Plant maintenance/asset management.
 
 
 ## Solution Architecture
 
The key services used from **Amazon Web Services** are AWS IoT SiteWise, Amazon S3, Amazon Lambda Function, AWS Secrets Manager. The services used from **SAP BTP** are the Cloud Foundry Runtime, SAP Integration Suite Advanced Event Mesh, SAP Connectivity service, SAP Private Link service, SAP Build Process Automation- Decisions, SAP HANA Cloud , SAP Business Application Studio and SAP Destination service, SAP AI Core, SAP AI Launchpad.

SAP Private Link service is used for connectivity between SAP BTP and SAP S/4HANA when both the systems are running on Amazon AWS Infrastructure, in this tutorial you will find implementation steps for SAP BTP Private Link service and AWS Private Link service. Alternatively you can use SAP Connectivity service and Cloud Connector for integration of SAP BTP and SAP S/4HANA as well.
 
 
 ![plot](./Solution-Architecture.png) **Figure-1: High-level architecture (with SAP S/4HANA on AWS)**
 
 The following steps depicts the information flow across systems:
 
(1) Event is triggered from AWS IoT SiteWise.

(2) and (3) The sensor data from AWS IoT SiteWise is dumped into the Amazon S3 bucket.

(4a) AWS Lambda is a serverless function, which will orchestrate the process of detecting a stream contains any alerts related to failure or warnings, and then the inference result is passed to SAP Integration Suite, Advanced Event Mesh.

(4b) AWS secrets manager is used to store credentials, these are used by the lambda function to provide payload to SAP Integration Suite, Advanced Event Mesh.

(5), (6) Event-to-Business-Action framework(extension app) processor module's endpoint is subscribed to SAP Integration Suite, Advanced Event Mesh, hence receives this event.

(7) Event-to-Business-Action framework(extension app) processor module leverages the Business Rules capability of SAP Build Process Automation to derive business action (for example, In this scenario, Plant Maintenance Notification creation in SAP S/4HANA system) based on certain characteristics of incoming event.

(8a), (8b) Event-to-Business-Action framework(extension app) calls Amazon Bedrock LLM model using Gen AI hub to generate summary of the event.

(9), (10), (11) Event-to-Business-Action framework (extension app) processor module triggers the defined action in the SAP S/4HANA system by using the SAP Destination Service and SAP Private Link Service.

For more information, see Set Up Connectivity Between SAP BTP and SAP S/4HANA Using SAP Private Link Service page.
 
 ## Requirements
 
 These are the technical prerequistics for an integration between AWS IoT Core, SAP BTP and SAP S/4HANA. 
 
 **Services in SAP BTP**
 - Cloud Foundry Runtime
     > - Foundation for running the CAP extension application for translating events to business actions.
 
 - Memory/Runtime quota
     > - Required for deploying and running the extension application in SAP BTP
 
 - Authorization & Trust Management Service
     > - Required for securing the extension application in SAP BTP
 
 - SAP Integration Suite,Advanced Event Mesh 
     >- Required to receive events from Amazon Monitron
 
 - SAP HANA Cloud 
     >- Required to store action configuration and logs for CAP application
 
 - SAP HANA Schemas & HDI Containers 
     >- Application database for CAP Application
 
 - SAP Build Process Automation - Decisions capability
     >- Decisions service to configure business decisions that needs to be taken based on the type of event received from Amazon Monitron.
 
 - SAP S/4HANA System
     >- To execute the business action associated with the event received. 
 
 - SAP Connectivity Service
     >- To establish connections between cloud applications and on-premise systems.
 
 - SAP Destination Service
     >- To find the destination information required to access a remote service or system from your extension application.
 
 - SAP Private Link Service
     >- To establishe a private connection between selected SAP BTP services and selected services in your own IaaS provider accounts.
 
 - SAP Business Application Studio
     >- A powerful and modern development environment, tailored for efficient development of business applications for the Intelligent Enterprise.
 
 **Amazon Web Services**
 - A valid AWS subscription
 
 - AWS IoTSiteWise
     > - Required for receiving and sending the events whenever an abnormality is detected in the equipment.
 
 - Amazon S3
     > - Required to store the received streaming event data.
 
 - AWS Secrets Manager
     >- Required to store the Advanced Event Mesh credentials that are accessed by the Amazon Lambda Function.
 
 - Amazon Lambda Function
     >- Required to orchestrate the process of detecting a stream contains any alerts related to failure or warnings, and then the inference result is passed to SAP Advanced Event Mesh.
 
 
 ## Additional Resources
 
 Related projects :
 
 - [Events-to-Business-Actions-Framework](https://github.com/SAP-samples/btp-events-to-business-actions-framework/tree/main)