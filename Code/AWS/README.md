## Integrating Amazon Monitron and SAP Plant maintenance
Amazon Monitron is an end-to-end system including hardware ( sensors and gateway) and software, that uses machine learning to detect abnormal conditions in industrial equipment and enable predictive maintenance. However, the output of machine learning in industrial operations only provides valuable results if action is taken on the machine learning insights. To reduce the burden of change management and ensure action is taken on the Monitron inferences, this sample project has demonstrated how to automatically record the Amazon Monitron inferences in SAP Plant maintenance/asset management.
From an SAP standpoint, we are only looking for inference data from Monitron. Without the actual hardware set up, This can be done in 2 ways
1) Use the [payload](/payload.json) file as a sample to integrate into SAP.
2) Use the [Kinesis data generator](https://awslabs.github.io/amazon-kinesis-data-generator/web/producer.html) and use the [template file](/kinesisdatatemplate.json)  to simulate a kinesis stream.The sample [output file](/kinesissample.txt) contains a seriesof json documents.
3) AN S3 bucket is a prerequisite for both these scenarios.

## Kinesis Data Generator ( Monitron Simulator)

Before generating data, please complete the following steps
1) Create an S3 bucket
2) Create a kinesis data stream and delivery stream as outlined [here](https://docs.aws.amazon.com/Monitron/latest/admin-guide/kinesis-store-S3.html)

[Kinesis data generator](https://awslabs.github.io/amazon-kinesis-data-generator/web/producer.html) can help simulate an output from Monitron. The template uses faker.js for variables. A [template file](./kinesisdatatemplate.json)
to generate the output is available in the github repo. Please make further modifications as necessary.
![Data Generator](/kinesisdatagen.png)
