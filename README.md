Most children with autism spectrum disorders (ASD) are visual learners. They tend to comprehend visual information better than auditory input, making visual supports more effective for their learning process.

The project was initiated due to the laborious creation of a visual card and a market demand for a better, cost-effective product. The aim is also to democratize AI, making it accessible to all and overcoming previous product limitations with the help of new technologies.

Visual aids product in the market: Bing Search Results / Can be quite costly Amazon Search Result
Applied behavior analysis (ABA) is a therapeutic approach for treating ASD.
Visual aids in applied behavior analysis (ABA) URL

 Overview
1. Switching between personas and modes of generation (List, Steps, Manual / Parents and Caregivers, Childs)
2. Visual Card generation and management (Set the order of images by Drag and Drop)
3. Vector Image search
4. Video generation from images (To teach work procedures)
5. Text-to-Image




Azure services ☁️:
1. Vector-based image search: Azure Cognitive Search & Computer Vision API for Vector embedding
2. Text-to-image generation: Azure OpenAI & Image Generation by Azure OpenAI Dall-E
3. Bing Image Search
4. Fluent emoji dataset
5. Azure Cognitive Services Speech to Text (Read the text on the card)
6. [Optional] Microsoft Coco dataset (Everyday Life Images)



 Installation and Setup

 Deploy to Azure 🪟: 
 Set parameters under infra\parameter.json
 Execute deploy.ps1 to upload the dataset, deploy Azure resources, initialize the database, and set up the search index.
 Open the backend directory. Deploy the application code to Azure App Service: It is recommended to use the Azure Extension in VS Code to deploy the code to Azure App Service. You can follow the Quickstart: Deploy a Python app
 The deployment step using Azure CLI, without relying on VS Code, is commented out in deploy.ps1. It requires SCM Basic Auth credentials.

 <# 
az webapp deployment source config-zip `
   --resource-group $ResourceGroup `
   --name $APP_SERVICE_NAME `
   --src "app.zip"
Write-Host "Application deployed to Azure App Service." 
#>

Please ensure you have installed nodejs, yarn, Azure CLI, Azure Functions Core Tools, psql, and python3.

# Install Chocolatey
Set-ExecutionPolicy Bypass -Scope Process -Force; `
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; `
iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))

# Install Node.js
choco install nodejs -y

# Install Yarn
choco install yarn -y

# Install Azure CLI
choco install azure-cli -y

# Install Azure Functions Core Tools
choco install azure-functions-core-tools -y

# Install PostgreSQL
choco install postgresql -y

# Install Python 3.11
choco install python --version 3.11.0 -y

To dev :
 1.Open project folder in Visual Studio Code
 2.Rename .env.template to .env, then fill in the values in .env.
 3.In the terminal, run yarn install.
 4.Run yarn run dev to view the project in a browser.
 5.Run yarn run dev to view the project in a browser.

 !important: react-beautiful-dnd was not able to work well with reactStrictMode: true in NextJs. Turn off the option at next.config.js.`

 TODO
 Option for PostgreSQL as a vector database
  Regularly removing unexpectedly failed or deleted data from the database, Azure AI Search, and Blob storage to maintain data consistency.
  Download: If an image URL points to a web address that is not stored in the blob, it should be downloaded using HTTPS.
 Key access to the Azure Storage Account for embedding API.
 Bug fix (wip): Script deployment issue fixed, and other bugs.














