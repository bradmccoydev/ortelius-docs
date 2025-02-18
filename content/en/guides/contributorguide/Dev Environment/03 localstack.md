---
title: "Localstack"
linkTitle: "Localstack"
weight: 5
description: >
  Localstack allows you to run AWS cloud locally
---

## [AWS Localstack](https://localstack.cloud/) The AWS Cloud on your local machine `OPTIONAL`
- A fully functional local cloud stack to Develop and test your cloud and serverless apps offline!
- AWS only at the time of writing
- [Getting started](https://docs.localstack.cloud/get-started/)
- [Localstack Docs](https://docs.localstack.cloud/overview/)
- [Integrations](https://docs.localstack.cloud/integrations/)
- [Localstack Cockpit Web UI](https://localstack.cloud/products/cockpit/) use this to make sure your services are running
- [AWS Feature Coverage](https://docs.localstack.cloud/aws/feature-coverage/)

![localstack docker!](images/localstack/localstack-docker.jpg)

## Integrations
- [Serverless Framework](https://docs.localstack.cloud/integrations/serverless-framework/)
- [Spring Cloud Function](https://docs.localstack.cloud/integrations/spring-cloud-function/)
- [Architect](https://docs.localstack.cloud/integrations/architect/)
- [AWS Copilot CLI](https://docs.localstack.cloud/integrations/copilot/)
- [Terraform](https://docs.localstack.cloud/integrations/terraform/)
- [Thundra](https://docs.localstack.cloud/integrations/thundra/)
- [AWS SAM](https://docs.localstack.cloud/integrations/aws-sam/)
- [AWS CDK](https://docs.localstack.cloud/integrations/aws-cdk/)
- [Pulumi](https://docs.localstack.cloud/integrations/pulumi/)
- [Kafka cluster](https://docs.localstack.cloud/integrations/kafka/)
- [AWS Chalice](https://docs.localstack.cloud/integrations/chalice/)

![integrations overview!](images/localstack/integrations-overview.png)

## Language SDKS

- [.NET](https://docs.localstack.cloud/integrations/sdks/dotnet/)
- [Go](https://docs.localstack.cloud/integrations/sdks/go/)
- [PHP](https://docs.localstack.cloud/integrations/sdks/php/)
- [Python: BOTO3](https://docs.localstack.cloud/integrations/sdks/python/)

## Requirements
- Docker installed & running
- [LocalStack CLI](https://docs.localstack.cloud/get-started/#localstack-cli)
- [Install AWS CLI](https://docs.localstack.cloud/integrations/aws-cli/)

## Up & Running
- Configure AWS Profile & Credentials
- Create a blank `config` & `credential` file with `vi` or `touch` & copy the below into each file

`.aws/config`
```
[default]
region = eu-central-1
output = yaml

[profile localstack]
region = eu-central-1
output = yaml
```
`.aws/credentials`
```
[localstack]
aws_access_key_id = test
aws_secret_access_key = test
```
- Start LocalStack from the command line `localstack start`
- Test you can hit a endpoint `aws --profile localstack --endpoint-url=http://localhost:4566 kinesis list-streams`

## Terraform
- Install Terraform
- Navigate to `terraform/` folder
- run `terraform init` then `terraform plan` then `terraform apply`
- Terraform configuration for a S3 bucket deployment including all the endpoints

`main.tf`
```
provider "aws" {
  access_key                  = "test"
  secret_key                  = "test"
  region                      = "eu-central-1"
  s3_force_path_style         = false
  skip_credentials_validation = true
  skip_metadata_api_check     = true
  skip_requesting_account_id  = true

  endpoints {
    apigateway     = "http://localhost:4566"
    apigatewayv2   = "http://localhost:4566"
    cloudformation = "http://localhost:4566"
    cloudwatch     = "http://localhost:4566"
    dynamodb       = "http://localhost:4566"
    ec2            = "http://localhost:4566"
    es             = "http://localhost:4566"
    elasticache    = "http://localhost:4566"
    firehose       = "http://localhost:4566"
    iam            = "http://localhost:4566"
    kinesis        = "http://localhost:4566"
    lambda         = "http://localhost:4566"
    rds            = "http://localhost:4566"
    redshift       = "http://localhost:4566"
    route53        = "http://localhost:4566"
    s3             = "http://s3.localhost.localstack.cloud:4566"
    secretsmanager = "http://localhost:4566"
    ses            = "http://localhost:4566"
    sns            = "http://localhost:4566"
    sqs            = "http://localhost:4566"
    ssm            = "http://localhost:4566"
    stepfunctions  = "http://localhost:4566"
    sts            = "http://localhost:4566"
  }
}

resource "aws_s3_bucket" "test-bucket" {
  bucket = "abs-bucket"
}
```

## Pulumi
- [Getting started with AWS](https://www.pulumi.com/docs/get-started/aws/)
- [AWS installation configuration](https://www.pulumi.com/registry/packages/aws/installation-configuration/)
- Pulumi endpoint configuration

`Pulumi.dev.yaml`
```
config:
  aws:accessKey: "test"
  aws:secretKey: "test"
  aws:profile: "localstack"
  aws:region: "eu-central-1"
  aws:s3UsePathStyle: "true"
  aws:skipCredentialsValidation: "true"
  aws:skipRequestingAccountId: "true"
  aws:endpoints:
    - accessanalyzer: http://localhost:4566
      account: http://localhost:4566
      acm: http://localhost:4566
      acmpca: http://localhost:4566
      alexaforbusiness: http://localhost:4566
      amp: http://localhost:4566
      amplify: http://localhost:4566
      amplifybackend: http://localhost:4566
      apigateway: http://localhost:4566
      apigatewayv2: http://localhost:4566
      appautoscaling: http://localhost:4566
      appconfig: http://localhost:4566
      appflow: http://localhost:4566
      appintegrations: http://localhost:4566
      appintegrationsservice: http://localhost:4566
      applicationautoscaling: http://localhost:4566
      applicationcostprofiler: http://localhost:4566
      applicationdiscovery: http://localhost:4566
      applicationdiscoveryservice: http://localhost:4566
      applicationinsights: http://localhost:4566
      appmesh: http://localhost:4566
      appregistry: http://localhost:4566
      apprunner: http://localhost:4566
      appstream: http://localhost:4566
      appsync: http://localhost:4566
      athena: http://localhost:4566
      auditmanager: http://localhost:4566
      augmentedairuntime: http://localhost:4566
      autoscaling: http://localhost:4566
      autoscalingplans: http://localhost:4566
      backup: http://localhost:4566
      batch: http://localhost:4566
      braket: http://localhost:4566
      budgets: http://localhost:4566
      chime: http://localhost:4566
      cloud9: http://localhost:4566
      cloudcontrol: http://localhost:4566
      cloudcontrolapi: http://localhost:4566
      clouddirectory: http://localhost:4566
      cloudformation: http://localhost:4566
      cloudfront: http://localhost:4566
      cloudhsm: http://localhost:4566
      cloudhsmv2: http://localhost:4566
      cloudsearch: http://localhost:4566
      cloudsearchdomain: http://localhost:4566
      cloudtrail: http://localhost:4566
      cloudwatch: http://localhost:4566
      cloudwatchevents: http://localhost:4566
      cloudwatchlogs: http://localhost:4566
      codeartifact: http://localhost:4566
      codebuild: http://localhost:4566
      codecommit: http://localhost:4566
      codedeploy: http://localhost:4566
      codeguruprofiler: http://localhost:4566
      codegurureviewer: http://localhost:4566
      codepipeline: http://localhost:4566
      codestar: http://localhost:4566
      codestarconnections: http://localhost:4566
      codestarnotifications: http://localhost:4566
      cognitoidentity: http://localhost:4566
      cognitoidentityprovider: http://localhost:4566
      cognitoidp: http://localhost:4566
      cognitosync: http://localhost:4566
      comprehend: http://localhost:4566
      comprehendmedical: http://localhost:4566
      config: http://localhost:4566
      configservice: http://localhost:4566
      connect: http://localhost:4566
      connectcontactlens: http://localhost:4566
      connectparticipant: http://localhost:4566
      costandusagereportservice: http://localhost:4566
      costexplorer: http://localhost:4566
      cur: http://localhost:4566
      databasemigration: http://localhost:4566
      databasemigrationservice: http://localhost:4566
      dataexchange: http://localhost:4566
      datapipeline: http://localhost:4566
      datasync: http://localhost:4566
      dax: http://localhost:4566
      detective: http://localhost:4566
      devicefarm: http://localhost:4566
      devopsguru: http://localhost:4566
      directconnect: http://localhost:4566
      dlm: http://localhost:4566
      dms: http://localhost:4566
      docdb: http://localhost:4566
      ds: http://localhost:4566
      dynamodb: http://localhost:4566
      dynamodbstreams: http://localhost:4566
      ec2: http://localhost:4566
      ec2instanceconnect: http://localhost:4566
      ecr: http://localhost:4566
      ecrpublic: http://localhost:4566
      ecs: http://localhost:4566
      efs: http://localhost:4566
      eks: http://localhost:4566
      elasticache: http://localhost:4566
      elasticbeanstalk: http://localhost:4566
      elasticinference: http://localhost:4566
      elasticsearch: http://localhost:4566
      elasticsearchservice: http://localhost:4566
      elastictranscoder: http://localhost:4566
      elb: http://localhost:4566
      elbv2: http://localhost:4566
      emr: http://localhost:4566
      emrcontainers: http://localhost:4566
      es: http://localhost:4566
      eventbridge: http://localhost:4566
      events: http://localhost:4566
      finspace: http://localhost:4566
      finspacedata: http://localhost:4566
      firehose: http://localhost:4566
      fis: http://localhost:4566
      fms: http://localhost:4566
      forecast: http://localhost:4566
      forecastquery: http://localhost:4566
      forecastqueryservice: http://localhost:4566
      forecastservice: http://localhost:4566
      frauddetector: http://localhost:4566
      fsx: http://localhost:4566
      gamelift: http://localhost:4566
      glacier: http://localhost:4566
      globalaccelerator: http://localhost:4566
      glue: http://localhost:4566
      gluedatabrew: http://localhost:4566
      greengrass: http://localhost:4566
      greengrassv2: http://localhost:4566
      groundstation: http://localhost:4566
      guardduty: http://localhost:4566
      health: http://localhost:4566
      healthlake: http://localhost:4566
      honeycode: http://localhost:4566
      iam: http://localhost:4566
      identitystore: http://localhost:4566
      imagebuilder: http://localhost:4566
      inspector: http://localhost:4566
      iot: http://localhost:4566
      iot1clickdevices: http://localhost:4566
      iot1clickdevicesservice: http://localhost:4566
      iot1clickprojects: http://localhost:4566
      iotanalytics: http://localhost:4566
      iotdataplane: http://localhost:4566
      iotdeviceadvisor: http://localhost:4566
      iotevents: http://localhost:4566
      ioteventsdata: http://localhost:4566
      iotfleethub: http://localhost:4566
      iotjobsdataplane: http://localhost:4566
      iotsecuretunneling: http://localhost:4566
      iotsitewise: http://localhost:4566
      iotthingsgraph: http://localhost:4566
      iotwireless: http://localhost:4566
      kafka: http://localhost:4566
      kafkaconnect: http://localhost:4566
      kendra: http://localhost:4566
      kinesis: http://localhost:4566
      kinesisanalytics: http://localhost:4566
      kinesisanalyticsv2: http://localhost:4566
      kinesisvideo: http://localhost:4566
      kinesisvideoarchivedmedia: http://localhost:4566
      kinesisvideomedia: http://localhost:4566
      kinesisvideosignalingchannels: http://localhost:4566
      kms: http://localhost:4566
      lakeformation: http://localhost:4566
      lambda: http://localhost:4566
      lexmodelbuilding: http://localhost:4566
      lexmodelbuildingservice: http://localhost:4566
      lexmodels: http://localhost:4566
      lexmodelsv2: http://localhost:4566
      lexruntime: http://localhost:4566
      lexruntimeservice: http://localhost:4566
      lexruntimev2: http://localhost:4566
      licensemanager: http://localhost:4566
      lightsail: http://localhost:4566
      location: http://localhost:4566
      lookoutequipment: http://localhost:4566
      lookoutforvision: http://localhost:4566
      lookoutmetrics: http://localhost:4566
      machinelearning: http://localhost:4566
      macie: http://localhost:4566
      macie2: http://localhost:4566
      managedblockchain: http://localhost:4566
      marketplacecatalog: http://localhost:4566
      marketplacecommerceanalytics: http://localhost:4566
      marketplaceentitlement: http://localhost:4566
      marketplaceentitlementservice: http://localhost:4566
      marketplacemetering: http://localhost:4566
      mediaconnect: http://localhost:4566
      mediaconvert: http://localhost:4566
      medialive: http://localhost:4566
      mediapackage: http://localhost:4566
      mediapackagevod: http://localhost:4566
      mediastore: http://localhost:4566
      mediastoredata: http://localhost:4566
      mediatailor: http://localhost:4566
      memorydb: http://localhost:4566
      mgn: http://localhost:4566
      migrationhub: http://localhost:4566
      migrationhubconfig: http://localhost:4566
      mobile: http://localhost:4566
      mobileanalytics: http://localhost:4566
      mq: http://localhost:4566
      mturk: http://localhost:4566
      mwaa: http://localhost:4566
      neptune: http://localhost:4566
      networkfirewall: http://localhost:4566
      networkmanager: http://localhost:4566
      nimblestudio: http://localhost:4566
      opsworks: http://localhost:4566
      opsworkscm: http://localhost:4566
      organizations: http://localhost:4566
      outposts: http://localhost:4566
      personalize: http://localhost:4566
      personalizeevents: http://localhost:4566
      personalizeruntime: http://localhost:4566
      pi: http://localhost:4566
      pinpoint: http://localhost:4566
      pinpointemail: http://localhost:4566
      pinpointsmsvoice: http://localhost:4566
      polly: http://localhost:4566
      pricing: http://localhost:4566
      prometheus: http://localhost:4566
      prometheusservice: http://localhost:4566
      proton: http://localhost:4566
      qldb: http://localhost:4566
      qldbsession: http://localhost:4566
      quicksight: http://localhost:4566
      ram: http://localhost:4566
      rds: http://localhost:4566
      rdsdata: http://localhost:4566
      rdsdataservice: http://localhost:4566
      redshift: http://localhost:4566
      redshiftdata: http://localhost:4566
      rekognition: http://localhost:4566
      resourcegroups: http://localhost:4566
      resourcegroupstagging: http://localhost:4566
      resourcegroupstaggingapi: http://localhost:4566
      robomaker: http://localhost:4566
      route53: http://localhost:4566
      route53domains: http://localhost:4566
      route53recoverycontrolconfig: http://localhost:4566
      route53recoveryreadiness: http://localhost:4566
      route53resolver: http://localhost:4566
      s3: http://localhost:4566
      s3control: http://localhost:4566
      s3outposts: http://localhost:4566
      sagemaker: http://localhost:4566
      sagemakeredgemanager: http://localhost:4566
      sagemakerfeaturestoreruntime: http://localhost:4566
      sagemakerruntime: http://localhost:4566
      savingsplans: http://localhost:4566
      schemas: http://localhost:4566
      sdb: http://localhost:4566
      secretsmanager: http://localhost:4566
      securityhub: http://localhost:4566
      serverlessapplicationrepository: http://localhost:4566
      serverlessapprepo: http://localhost:4566
      serverlessrepo: http://localhost:4566
      servicecatalog: http://localhost:4566
      servicediscovery: http://localhost:4566
      servicequotas: http://localhost:4566
      ses: http://localhost:4566
      sesv2: http://localhost:4566
      sfn: http://localhost:4566
      shield: http://localhost:4566
      signer: http://localhost:4566
      simpledb: http://localhost:4566
      sms: http://localhost:4566
      snowball: http://localhost:4566
      sns: http://localhost:4566
      sqs: http://localhost:4566
      ssm: http://localhost:4566
      ssmcontacts: http://localhost:4566
      ssmincidents: http://localhost:4566
      sso: http://localhost:4566
      ssoadmin: http://localhost:4566
      ssooidc: http://localhost:4566
      stepfunctions: http://localhost:4566
      storagegateway: http://localhost:4566
      sts: http://localhost:4566
      support: http://localhost:4566
      swf: http://localhost:4566
      synthetics: http://localhost:4566
      textract: http://localhost:4566
      timestreamquery: http://localhost:4566
      timestreamwrite: http://localhost:4566
      transcribe: http://localhost:4566
      transcribeservice: http://localhost:4566
      transcribestreaming: http://localhost:4566
      transcribestreamingservice: http://localhost:4566
      transfer: http://localhost:4566
      translate: http://localhost:4566
      waf: http://localhost:4566
      wafregional: http://localhost:4566
      wafv2: http://localhost:4566
      wellarchitected: http://localhost:4566
      workdocs: http://localhost:4566
      worklink: http://localhost:4566
      workmail: http://localhost:4566
      workmailmessageflow: http://localhost:4566
      workspaces: http://localhost:4566
      xray: http://localhost:4566
```