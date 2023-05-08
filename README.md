# OCR workflow examples

The workflow will do Optical Character Recognition (OCR) on images uploaded to Azure Storage containers and email the results to a user

## Workflow overview

For the OCR workflows, you need to know the following:
- To start the OCR workflow, we have added 2 files (images) to the GitHub repository you can use.
- You can upload the images using to your Azure Storage container. Ability to upload to an Azure Storage Container, with Azure Events configured to send to Direktiv namespace (https://docs.direktiv.io/events/cloud/azure/). Example screenshots have been included in the repository. to the Pay-As-You-Go/Storage Accounts/Direktiv/Blob Containers/upload directory (see the attached screenshot).
- Once you upload the file, an event is fired off to the configured Direktiv instance, in the appropriate namespace.
- The workflow will analyse the image and convert it to text.
- It will send a message to the Slack channel with the message and the image.
- It will send an email to recipients configured in the workflow. The email contains the OCR text as an attachment and the URL to the original file you uploaded.
- It will also send a Teams message with the details.

*You need the following components to run this workflow:*
- Ability to upload to an Azure Storage Container, with Azure Events configured to send to Direktiv namespace (https://docs.direktiv.io/events/cloud/azure/). Example screenshots have been included in the repository.
 
 ## Variables

 - email-template.tpl: Mustache email template to create an HTML template with original message and new links

## Secrets

 - EMAIL_USER, EMAIL_PASSWORD: email acccess credentials
 - SLACK_URL: Slack channel URL
 - TEAMS_WEBHOOK_URL: Microsoft Teams application channel

## Namespace Services

 - None

## Input examples

Example input to the workflow for a decomposed email:

```json
{
  "Microsoft.Storage.BlobCreated": {
    "data": {
      "api": "PutBlob",
      "blobType": "BlockBlob",
      "clientRequestId": "f9146d76-246b-4fec-75e3-5b8e5daa0c68",
      "contentLength": 602091,
      "contentType": "image/png",
      "eTag": "0x8DB500B45DF658D",
      "requestId": "feaf5f0b-e01e-0038-4ef4-814210000000",
      "sequencer": "00000000000000000000000000010C26000000000067dc78",
      "storageDiagnostics": {
        "batchId": "efa5d22c-2006-006a-00f4-813ef8000000"
      },
      "url": "https://direktiv.blob.core.windows.net/upload/direktiv-overview.png"
    },
    "id": "feaf5f0b-e01e-0038-4ef4-8142100607cf",
    "source": "/subscriptions/40eb3cb3-a114-4cd1-b584-5bbedd2126a2/resourceGroups/vorteil-demo/providers/Microsoft.Storage/storageAccounts/direktiv",
    "specversion": "1.0",
    "subject": "/blobServices/default/containers/upload/blobs/direktiv-overview.png",
    "time": "2023-05-08T21:29:15.0197922Z",
    "type": "Microsoft.Storage.BlobCreated"
  }
}
```

## External links:

 - Blog article: https://blog.direktiv.io/turn-your-code-into-a-serverless-api-748490acd470ß