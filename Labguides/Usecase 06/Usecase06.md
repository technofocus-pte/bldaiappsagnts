# Usecase 06- Develop an AI-Powered Copilot for Financial Advisors with Microsoft Foundry

#### **Overview**

A custom copilot powered by Azure OpenAI and Foundry Tools that
streamlines daily tasks and customer meeting preparation for
customer-facing roles. As a result, this helps to improve client
retention and customer satisfaction. By increasing employee productivity
and improving customer conversations, our solution enables organizations
to serve more customers and drive increased revenue for the entire
company.

#### **Scenario**

![A screenshot of a computer AI-generated content may be incorrect.](./media/image1.png)

A Woodgrove Bank Client Advisor is preparing for upcoming client
meetings. He wants insight into his scheduled client meetings, access to
portfolio information, a comprehensive understanding of previous
meetings, and the ability to ask questions about client’s financial
details and interests.

This solution has an integrated copilot that helps Client Advisors to
save time and prepare relevant discussion topics for scheduled meetings.
It provides an overview of daily client meetings with seamless
navigation between viewing client profiles and chatting with data.
Altogether, these features streamline meeting preparation for client
advisors and result in more productive conversations with clients.

![A diagram of a company AI-generated content may be incorrect.](./media/image2.png)

**Solution overview**

Leverages Azure OpenAI Service and Azure AI Search, this solution
streamlines daily tasks and customer meeting preparation for
customer-facing roles. As a result, this helps to improve client
retention and customer satisfaction. By increasing employee productivity
and improving customer conversations, our solution enables organizations
to serve more customers and drive increased revenue for the entire
company.

**Business value**

- **Reduce expenses, increase revenue**  
  Copilots can reduce operational costs, enhance revenue, and maintain
  competitiveness.

- **Enhance productivity**  
  Copilots save professionals time in the meeting preparation process
  which enables them to handle more tasks and increase customer
  satisfaction.

- **Talent retention**  
  Organizations can empower employees to deliver the best customer
  experiences with a focus on relationships, resulting in higher morale
  and the retention of top talent.

- **Enhance customer engagement**  
  Copilots can support improved customer interactions for enhanced
  satisfaction, and enabling professionals to serve a greater number of
  customers.

- **Optimize daily tasks**  
  Copilots can streamline workflows by providing intelligent summaries,
  recommended action items, integrated client views, and immediate
  support through conversational interfaces.

**Introduction**

This use case guides you through building an AI-powered copilot for
financial advisors using Microsoft Foundry, Azure OpenAI, and Azure AI
Search. The solution is designed to enhance the daily workflow of
customer-facing roles by providing instant access to client meeting
summaries, portfolio insights, and conversational financial analysis. By
automating time-consuming research and preparation tasks, the copilot
empowers advisors to deliver more informed, personalized, and productive
client interactions. Throughout this lab, you will provision Azure
resources, process sample financial data, deploy a working copilot
application, and explore how AI can significantly improve advisor
efficiency, customer satisfaction, and overall business impact

**Objectives**

- Understand how an AI copilot improves productivity and client
  engagement for financial advisors.

- Deploy Azure resources required for the copilot solution using Azure
  Developer CLI.

- Set up and configure GitHub Codespaces for cloud-based development.

- Upload and process sample financial datasets for use in the
  application.

- Explore the deployed copilot’s capabilities for meeting summaries,
  client insights, and portfolio analysis.

- Integrate authentication within Azure App Service for secure access to
  the copilot application.

- Validate data retrieval and conversational capabilities using sample
  queries.

- Learn how Azure OpenAI and Azure AI Search power real-time insight
  generation in customer-facing scenarios.

**Prerequisites**

- **GitHub Account**: You are expected to have your own GitHub login
  credentials.  
  If you do not have an account, please create one by visiting:  
  +++https://github.com/signup?user_email=&source=form-home-signup+++

## Task 0: Understand the VM and the credentials

In this task, we will identify and understand the credentials that we
will be using throughout the lab.

1.  **Instructions** tab hold the lab guide with the instructions to be
    followed throughout the lab.

2.  **Resources** tab has got the credentials that will be needed for
    executing the lab.

    - **URL** – URL to the Azure portal

    - **Subscription** – This is the ID of the subscription assigned to
      you

    - **Username** – The user id with which you need to login to the
      Azure services.

    - **Password** – Password to the Azure login. Let us call this
      Username and password as Azure login credentials. We will use
      these creds wherever we mention Azure login credentials.

    - **Resource Group** – The **Resource group** assigned to you.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image3.png)

3.  **Help** tab holds the Support information. The **ID** value here is
    the **Lab instance ID** which will be used during the lab execution.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image4.png)

    >[!Note] Make sure you create all your resources under this resource group.

## Task 1: Register Service provider

1.  Open a browser go to +++https://portal.azure.com+++ and sign in with
    your cloud slice account below.

    Username: +++@lab.CloudPortalCredential(User1).Username+++
    
    Password: +++@lab.CloudPortalCredential(User1).AccessToken+++

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image5.png)

    ![A login box with a red box and blue box with text AI-generated content may be incorrect.](./media/image6.png)

2.  Click on **Subscriptions** tile.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image7.png)

3.  Click on the subscription name.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image8.png)

4.  Expand Settings from the left navigation menu. Click on **Resource
    providers**, enter **+++** **Microsoft.CognitiveServices+++** and
    select i,t, and then click **Register**.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image9.png)
    
    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image10.png)
    
    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image11.png)

## Task 2: Open Github Codespaces environment

1.  Open your browser, navigate to the address bar, type or paste the
    following URL: +++https://github.com/microsoft/Build-your-own-copilot-Solution-Accelerator+++

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image12.png)

2.  Click on **fork** to fork the repo. Give unique name to the repo and
    click on **Create repo** button.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image13.png)

3.  Click on **Code -\> Codespaces -\> Codespaces+**

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image14.png)

4.  Wait for the Codespaces environment to setup .It takes few minutes
    to setup completely

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image15.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image16.png)

## Task 3: Provision Services and deploy application to Azure

1.  Run the following command on the Terminal. It generates the code to
    copy. Copy the code and press Enter.

    +++azd auth login+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image17.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image18.png)

2.  Default browser opens to enter the generated code to verify. Enter
    the code and click **Next**.

    ![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image19.png)

3.  Sign in with your Azure credentials.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image20.png)

    ![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image21.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image22.png)

4.  Run the following commands to set the resource location region and to deploy the necessary resources - This will provision Azure resources

    +++azd env set AZURE_LOCATION centralus+++
    
    +++azd up+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image23.png)

6.  Enter +++byocaapp@lab.labinstance.id+++ as your environment name.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image24.png)

7.  Select below values.

    - **Select an Azure Subscription to use** : Select your subscription
    
    - **azureAiServiceLocation**: Sweden Central
    
    - **‘location' infrastructure parameter:** @lab.CloudResourceGroup(ResourceGroup1).Location
    
    - **Pick a resource group to use:** @lab.CloudResourceGroup(ResourceGroup1).Name

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image25.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image26.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image27.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image28.png)

8.  This deployment will take *7-10 minutes* to provision the resources
    in your account and set up the solution with sample data.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image29.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image30.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image31.png)

9.  Now the deployment is complete

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image32.png)

10.  After the application has been successfully deployed, you see a URL
    displayed in the terminal. Copy the **URL**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image33.png)

## Task 4:Import Sample Data

1.  Run the sample data processing script by executing **bash
    ./infra/scripts/process_sample_data.sh** from the project root to
    prepare and upload the required data.

    +++bash ./infra/scripts/process_sample_data.sh+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image34.png)

2.  After running the command **bash
    ./infra/scripts/process_sample_data.sh**, authenticate in the
    browser by opening +++https://microsoft.com/devicelogin+++
    and entering the **displayed code** to continue the script
    execution.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image35.png)

    ![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image36.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image37.png)

3.  Select your subscription

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image38.png)

    ![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image39.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image40.png)

    ![A screenshot of a computer program AI-generated content may be
incorrect.](./media/image41.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image42.png)

## Task 5: Verify deployed resources in the Azure portal

1.  Select **Resource groups**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image43.png)

2.  Click on your assigned **Resource group**.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image44.png)

3.  Make sure the below resource got deployed successfully

    - Foundry
    
    - Foundry project
    
    - App Service
    
    - Container registry
    
    - Azure Cosmos DB account
    
    - SQL server
    
    - SQL Database
    
    - Search service
    
    - Azure Storage account

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image45.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image46.png)

4.  On the resource group and click on **Azure Storage account.**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image47.png)

5.  From the left navigation menu, click on **Containers** , Make sure
    data should be deployed successfully

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image48.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image49.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image50.png)

6.  Go back to resorcegroup and click on **Foundry Project.**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image51.png)

3.  Click **Go to Foundry portal** to verify that the model has been
    successfully deployed.

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image52.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image53.png)

## Task 6: Add Authentication in Azure App Service configuration

1.  Go back to resorcegroup and click on **App
    Service(app-byocaappXXX).**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image54.png)

2.  On the web app home page, go to **Settings** and click
    **Authentication** from the left menu

    ![A screenshot of a computer AI-generated content may be incorrect.](./media/image55.png)

4.  Click on **Add identity provider** to see a list of identity
    providers.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image56.png)

5.  Click on Identity Provider dropdown to see a list of identity
    providers and select the first option **Microsoft** from the
    drop-down list 

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image57.png)

6.  Select **client secret expiration** under App registration and click
    on **Add** button

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image58.png)

7.  You have successfully added app authentication, and now required to
    log in to access the application.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image59.png)

6.  On the web app home page, go to **Overview** and click **Browse**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image60.png)

7.  Wait for the web application deployment to complete.

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image61.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image62.png)

## Task 7: Review and Explore the Sample Questions for Your Copilot Application

To help you get started, here are some **Sample Prompts** you can ask
after selecting the **Karen Berg** client:

1.  Click on **Karen Berg** client

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image63.png)

2.  On the web app page, enter the following question and click the
    **Submit** icon as shown in the image.

    +++What were Karen's concerns during our last meeting?+++

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image64.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image65.png)

3.  On the web app page, enter the following question and click the
    **Submit** icon as shown in the image.
    
    +++Did Karen express any concerns over market fluctuations in prior meetings?+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image66.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image67.png)

4.  On the web app page, enter the following question and click the
    **Submit** icon as shown in the image

    +++What type of asset does Karen own ?+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image68.png)

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image69.png)

    +++ Show latest asset value by asset type?+++

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image70.png)

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image71.png)

    +++How did equities asset value change in the last six months?+++

    ![A screenshot of a chat AI-generated content may be
incorrect.](./media/image72.png)

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image73.png)

This structured approach helps users quickly retrieve client-specific
insights, track financial trends, and stay informed on client priorities
for better decision-making and engagement.

## Task 8: Delete the Resources

1.  To delete Resource group , type **Resource groups** in the Azure
    portal search bar, navigate and click on **Resource
    groups** under **Services**.

    ![A screenshot of a computer Description automatically generated](./media/image74.png)

2.  In the Resource groups page, select your resource group.

3.  In the **Resource group** home page, select all resources and click
    on **delete**

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image75.png)

4.  In the **Delete Resources** pane that appears on the right side,
    navigate to **Enter “delete” to confirm deletion** field, then click
    on the **Delete** button

    ![A screenshot of a computer AI-generated content may be
incorrect.](./media/image76.png)

5.  On **Delete confirmation** dialog box, click on **Delete** button.

    ![A screenshot of a computer error AI-generated content may be
incorrect.](./media/image77.png)

**Summary**

This usecase explains how to deploy and use a custom AI copilot built
with Azure OpenAI and Azure AI Search to support customer-facing roles,
such as financial client advisors. The copilot streamlines daily work by
summarizing past client meetings, providing financial insights, and
enabling conversational data queries, ultimately improving customer
satisfaction, retention, and productivity. The document walks learners
through provisioning Azure resources using Azure Developer CLI (azd up),
processing and uploading sample data, verifying deployed services such
as App Service, Cosmos DB, SQL Database, Azure Storage, and Foundry
projects, and configuring authentication for secure access. Users then
explore the deployed web application and test sample prompts to retrieve
client insights, such as past concerns, asset details, and financial
trends. The lab concludes with cleanup steps for deleting the resource
group. Overall, the guide provides an end-to-end hands-on experience for
building and deploying a working copilot application in Azure.
