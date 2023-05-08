# OCR workflow examples

For the OCR workflows, you need to know the following:
 
- Download the Azure Storage Explorer from https://www.macupdate.com/app/mac/63165/microsoft-azure-storage-explorer/download
- Once you have this downloaded, you’ll need to log in with my account (for the first time you’ll need a PIN, so let me know when you’re ready).
- To start the OCR workflow, I have added 2 files (images) to the GitHub repository you can use (https://github.com/wwonigkeit/ocr-workflows) – Corne has access to this.
- You can upload the images using the Azure Storage Explorer to the Pay-As-You-Go/Storage Accounts/Direktiv/Blob Containers/upload directory (see the attached screenshot).
- Once you upload the file, an event is fired off to the https://equinix.direktiv.io instance, in the ocr-workflow namespace.
- The workflow will analyse the image and convert it to text.
- It will send a message to the Slack channel with the message and the image (https://direktiv-io.slack.com/archives/C0458KRA163). I think Corné has access to this.
- It will send an email to wwonigkeit@iqconsult.com.au, cgrobbelaar@iqconsult.com.au and matthewwebster@iqconsult.com.au. The email contains the OCR text as an attachment and the URL to the original file you uploaded.
- It will also send a Teams message with the details to https://teams.microsoft.com/l/channel/19%3aec1257cc7737472eab23ebc9d159316d%40thread.tacv2/DirektivTestChannel?groupId=e733ede8-6e15-4611-9ed9-074b718409c6&tenantId=a9397321-5af1-4fc3-8a7f-92820f7b574d. You both should have access to this (please test it).
 