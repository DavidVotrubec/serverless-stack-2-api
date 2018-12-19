# Serverless Stack Demo API

[Serverless Stack](http://serverless-stack.com) is a free comprehensive guide to creating full-stack serverless applications. We create a [note taking app](http://demo.serverless-stack.com) from scratch.

This repo is for the serverless backend API that we build over the course of the tutorial. You can find the repo for the frontend React app [here](https://github.com/AnomalyInnovations/serverless-stack-demo-client). And the repo for the tutorial [here](https://github.com/AnomalyInnovations/serverless-stack-com).

## My notes
Make sure that correct aws user is selected in the `serverless deploy` command. Otherwise it may fail with invalid credentials. See https://serverless.com/framework/docs/providers/aws/guide/credentials/

So in my case I will use `serverless deploy --aws-profile serverless-agent`

```
Service Information
service: notes-app-2-api
stage: dev
region: eu-central-1
stack: notes-app-2-api-dev
api keys:
  None
endpoints:
  POST - https://xhirdc72na.execute-api.eu-central-1.amazonaws.com/dev/notes
  GET - https://xhirdc72na.execute-api.eu-central-1.amazonaws.com/dev/notes/{id}
  GET - https://xhirdc72na.execute-api.eu-central-1.amazonaws.com/dev/notes
  PUT - https://xhirdc72na.execute-api.eu-central-1.amazonaws.com/dev/notes/{id}
  DELETE - https://xhirdc72na.execute-api.eu-central-1.amazonaws.com/dev/notes/{id}
functions:
  create: notes-app-2-api-dev-create
  get: notes-app-2-api-dev-get
  list: notes-app-2-api-dev-list
  update: notes-app-2-api-dev-update
  delete: notes-app-2-api-dev-delete
layers:
  None

Stack Outputs
AttachmentsBucketName: notes-app-2-api-dev-attachmentsbucket-rl04sguencvu
UserPoolClientId: 5j46c1o8uj62gv09pq3da10r38
UserPoolId: eu-central-1_GJNxJ5Dvg
DeleteLambdaFunctionQualifiedArn: arn:aws:lambda:eu-central-1:468609376333:function:notes-app-2-api-dev-delete:1
CreateLambdaFunctionQualifiedArn: arn:aws:lambda:eu-central-1:468609376333:function:notes-app-2-api-dev-create:1
GetLambdaFunctionQualifiedArn: arn:aws:lambda:eu-central-1:468609376333:function:notes-app-2-api-dev-get:1
UpdateLambdaFunctionQualifiedArn: arn:aws:lambda:eu-central-1:468609376333:function:notes-app-2-api-dev-update:1
IdentityPoolId: eu-central-1:64a349d1-2361-4949-8aa1-52a51233f67a
ListLambdaFunctionQualifiedArn: arn:aws:lambda:eu-central-1:468609376333:function:notes-app-2-api-dev-list:1
ServiceEndpoint: https://xhirdc72na.execute-api.eu-central-1.amazonaws.com/dev
ServerlessDeploymentBucketName: notes-app-2-api-dev-serverlessdeploymentbucket-4w543v0eg0ex
```

#### Steps

To support the different chapters and steps of the tutorial; we use branches to represent the project codebase at the various points. Here is an index of the various chapters and branches in order.

- [Set up the Serverless Framework](../../tree/setup-the-serverless-framework)
- [Add Support for ES6/ES7 JavaScript](../../tree/add-support-for-es6-es7-javascript)
- [Add a Create Note API](../../tree/add-a-create-note-api)
- [Add a Get Note API](../../tree/add-a-get-note-api)
- [Add a List All the Notes API](../../tree/add-a-list-all-the-notes-api)
- [Add an Update Note API](../../tree/add-an-update-note-api)
- [Add a Delete Note API](../../tree/add-a-delete-note-api)

#### Usage

To use this repo locally you need to have the [Serverless framework](https://serverless.com) installed.

``` bash
$ npm install serverless -g
```

Clone this repo and install the NPM packages.

``` bash
$ git clone https://github.com/AnomalyInnovations/serverless-stack-demo-api
$ npm install
```

Run a single API on local.

``` bash
$ serverless invoke local --function list --path event.json
```

Where, `event.json` contains the request event info and looks something like this.

``` json
{
  "requestContext": {
    "authorizer": {
      "claims": {
        "sub": "USER-SUB-1234"
      }
    }
  }
}
```

Finally, run this to deploy to your AWS account.

``` bash
$ serverless deploy -v
```

-v means "verbose"

#### Maintainers

Serverless Stack is authored and maintained by Frank Wang ([@fanjiewang](https://twitter.com/fanjiewang)) & Jay V ([@jayair](https://twitter.com/jayair)). [**Subscribe to our newsletter**](http://eepurl.com/cEaBlf) for updates on Serverless Stack. Send us an [email][Email] if you have any questions.

[Email]: mailto:contact@anoma.ly
