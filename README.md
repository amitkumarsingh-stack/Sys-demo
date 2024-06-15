## Sample Voting Application Workflow
This GitHub Actions workflow automates the deployment process to an Azure Kubernetes Service (AKS) whenever code is pushed to the main branch.

### Workflow Details
#### Trigger
* Trigger: Push to the main branch

#### Job Details
`build-and-deploy` Job:
* Runs on: ubuntu-latest with Node.js 20
#### Steps:
1. #### Checkout Repository:
* Uses actions/checkout@v4 to fetch the repository's code with full history.
2. #### Azure Login:
* Uses azure/login@v2 to authenticate with Azure using service principal credentials stored in GitHub secrets (AZURE_CRED).
3. #### Setup kubectl:
* Uses azure/setup-kubectl@v1 to configure kubectl with the latest version.
4. #### Retrieve AKS Credentials:
* Runs az aks get-credentials command to fetch credentials for the AKS cluster named sysdig-demo in the Sysdig-RG resource group.
5. #### List AKS Nodes:
* Verifies the connection to AKS by listing nodes using kubectl get nodes.
6. #### Promote to Production:
* Placeholder step to promote the deployment to production or perform additional post-deployment tasks.
## Notes
* Uncomment and modify Step 6 (kubectl apply -f k8s-specifications/) to deploy resources defined in your Kubernetes manifest files (k8s-specifications/).

### Usage Instructions
1. #### Prerequisites:

* Ensure you have Azure credentials (AZURE_CRED) configured in your GitHub repository secrets.
* Have necessary permissions to access and modify the AKS cluster (sysdig-demo in Sysdig-RG).
2. #### Deployment:

* Push changes to the main branch to trigger this workflow.
* Monitor workflow execution and logs in the Actions tab of your GitHub repository.

3. #### Customization:

* Modify the workflow steps (main.yml) as per your deployment requirements.
* Adjust Kubernetes manifest paths and deployment logic to fit your application needs.
Feedback:





