
## Prerequisites

Before you begin, make sure you have the following:

- [UiPath Account](https://cloud.uipath.com/portal_/cloudrpa)
- [UiPath Studio](https://download.uipath.com/UiPathStudioCommunity.msi) installed on your machine.
- Access to [UiPath Orchestrator](https://www.uipath.com/platform-trial) with appropriate permissions to create folders and queues.



## How to Use

Follow these 3 simple steps to use this project:

1. Make a folder named `ACME` in UiPath Orchestrator within your account.
2. Create a queue named `workItem` in the `ACME` folder in Orchestrator.
3. Open the [Main.xaml](Main.xaml) file of this project, 'RE_for_ACME', in UiPath Studio using the same account in which the queue and folder were created. Then, run the project.



## How It Works

### 1. Initialize Process

- **InitiAllSettings:** Loads configuration data from the [Config.xlsx](Data/Config.xlsx) file and from assets.
- **GetAppCredential:** Retrieves credentials from Orchestrator assets or local Windows Credential Manager.
- **InitiAllApplications:** Opens and logs in to applications used throughout the process.
  - This workflow invokes [AcmeLogin.xaml](Framework/Custom/AcmeLogin.xaml) to log in if not already logged in. 
  - It also invokes [FetchWorkItem.xaml](Framework/Custom/FetchWorkItems.xaml) to fetch Work-Items and push it into Orchestrator Queue.
  - In login try tu use the acount that already exist in my case i had to use a default account "duttthakur444@gmail.com" "0987654321@ACME" because i had a problem donwloading the files "Error 404"

### 2. Get Transaction Data

- **GetTransactionData:** Fetches transactions from an Orchestrator queue defined by `Config("OrchestratorQueueName")` or any other configured data source.

### 3. Process Transaction

- **Process:** Processes the transaction and invokes other workflows related to the specific automation process.
    - This workflow processes the transaction and invokes [ProcessQueueItem.xaml](Framework/Custom/ProcessQueueTransactions.xaml) to process the each Transactions of Queue.
    Change in the task read pdf the name of the link where you going to download the files


