
# Build Agentic intelligence with Microsoft Fabric IQ and Foundry IQ

## Introduction

Modern AI applications need more than just a model and a prompt — they
need **trusted business context, connected enterprise data, and the
ability to reason across both structured and unstructured information**.
In most organizations, however, that knowledge is scattered across
analytics platforms, documents, operational systems, and
line-of-business applications, making it difficult for AI agents to
generate responses that are both relevant and grounded.

This lab introduces a modern approach to solving that challenge by
bringing together the strengths of **Microsoft Fabric IQ** and
**Microsoft Foundry IQ** to build **agentic applications grounded in a
unified data foundation**. Microsoft Fabric IQ helps make enterprise
data more accessible and actionable by connecting insights across
analytical workloads, while Foundry IQ extends that intelligence by
enabling AI experiences that can understand, retrieve, and reason over
enterprise knowledge in a more contextual and agent-ready way.

By the end of this lab, you will have explored how a unified data estate
can serve as the grounding layer for intelligent agents, and how Fabric
IQ and Foundry IQ together can help transform raw enterprise data into
**usable, explainable, and business-ready AI experiences**.

![image](./media/image1.png)

## Objective

The primary objective of this lab is to help you **build and understand
an agentic AI solution that is grounded in unified enterprise data and
knowledge** by using Microsoft Fabric IQ and Foundry IQ together.

More specifically, this lab is designed to help you:

- **Understand the architecture of agentic applications** and how they
  differ from traditional chatbots or isolated AI copilots.

- Learn how **Microsoft Fabric IQ** can serve as a foundation for
  connecting and exposing business-relevant analytical data.

- Explore how **Microsoft Foundry IQ** can enhance AI experiences by
  making enterprise knowledge more discoverable, contextual, and usable
  for intelligent reasoning.

- Build a solution that can **retrieve, interpret, and respond using
  trusted organizational context** rather than relying only on model
  memory or static prompts.

- See how AI agents can be grounded in a **unified data foundation**
  that spans both **structured data** (such as business metrics,
  records, or analytical models) and **unstructured knowledge** (such as
  documents, policies, notes, or operational content).

- Understand how to design AI experiences that are more **accurate,
  explainable, relevant, and enterprise-ready**.

- Gain hands-on familiarity with the patterns, workflows, and
  implementation concepts needed to move from **data and insight** to
  **intelligent action**.

## Exercise 1: Deploy Infrastructure

In this exercise, you will deploy the architecture and resources to
Azure.

1.  Login to <https://github.com> using your own login credentials. If
    you don’t have a GitHub account, please create one here - https://github.com/signup .

2.  Open the GitHub repo - https://github.com/technofocus-pte/msfndryagenticAI
    and select **Fork** - > **Create fork** to create a copy of this
    repo in your GitHub account

3.  Once the repo is forked, select the dropdown next to Code. Select
    **Create codespaces on main** under the **Codespaces** tab.

    ![](./media/image2.png)

4.  The codespace creation takes around 5 to 10 minutes to complete.
    Once done, execute the command **azd auth login** from the terminal
    in order to deploy the Azure resources.

    ![](./media/image3.png)

5.  **Copy** the **next code** and select **Enter**. **Paste** the
    copied code in the browser, and continue to follow the prompts until
    logged in.

    ![](./media/image4.png)

6.  Back in terminal, execute **az login** to login to Azure CLI.

    ![](./media/image5.png)

7.  Click **Enter** to select the assigned subscription.

    ![](./media/image6.png)

8.  Execute the command **azd up**. Enter a unique environment name –
    envtxxxxx.

    ![](./media/image7.png)

9.  Choose a region.

10. Create a new resource group. Select the region for the Resource
    group, and accept the suggested Resource group name.

    ![](./media/image8.png)

11. This will deploy all the Azure resources and will take around 10
    minutes to complete.

    ![](./media/image9.png)
    
    ![](./media/image10.png)
    
    ![](./media/image11.png)

## Exercise 2: Create Fabric capacity

In this exercise, you will create the Fabric capacity required for the
upcoming exercises.

1.  Login to the Azure portal at <https://portal.azure.com> using the
    provided login credentials.

2.  From the **Home** page, search for and select **Microsoft Fabric**.

    ![](./media/image12.png)

3.  Select **+ Create** in the Fabric page.

    ![](./media/image13.png)

4.  Enter the below details and select **Review + create**.

    - Resource group – rg-xxxxxx
    
    - Capacity name - fcxxxxx
    
    - Size – F8
    
    ![](./media/image14.png)
    
    ![](./media/image15.png)

5.  Once the validation is complete, select **Create** to create the
    Fabric capacity.

    ![](./media/image16.png)

6.  Ensure that the resource is created properly.

    ![](./media/image17.png)

## Exercise 3: Create Fabric Workspace

In this exercise, you will create a Fabric Workspace that is required
for the upcoming exercises.

1.  Open
    <https://app.fabric.microsoft.com/home?experience=fabric-developer>
    and select **+ New workspace**.

    ![](./media/image18.png)

2.  Enter the name as **fabriciqxxxxxx**

    ![](./media/image19.png)

3.  Select **Fabric** and then select the created **Fabric capacity**
    and select **Apply**.

    ![](./media/image20.png)
    
    ![](./media/image21.png)

4.  From the url, copy the highlighted part in the screenshot below to a
    notepad. This is your workspace id.

    ![](./media/image22.png)

## Exercise 4: Setup Python environment

In this exercise, you will set up the environment required for the
execution.

1.  Back in the codespace terminal, execute the below command to create
    a virtual environment.

    python -m venv .venv

    ![](./media/image23.png)

2.  Execute the below command to activate the scripts.

    source .venv/bin/activate

    ![](./media/image24.png)

3.  Execute the below command to install the requirements.

    pip install uv && uv pip install -r scripts/requirements.txt
    
    ![](./media/image25.png)
    
    ![](./media/image26.png)

## Exercise 5: Build the solution

You will build the solution in this exercise.

1.  In the below command, replace \<your-workspace-id\> with the value
    saved from the **Fabric workspace url** in the earlier exercise and
    then execute the command.

    ![](./media/image27.png)
    
    ![](./media/image28.png)

2.  Once it loads the lists the actions and prompt to Enter/Cancel,
    press **Enter** to continue.

    ![](./media/image29.png)

3.  This builds the solution. It creates the Fabric Lakehouse and loads
    data into it. It creates the Fabric data agent and Microsoft Foundry
    agent and creates and adds the knowledge base to the Foundry IQ. It
    also deploys the app and gives the url.

    ![](./media/image30.png)

## Exercise 6: Test the agent through application

In this, you will test the application

1.  Click on the url in the terminal output.

    ![](./media/image31.png)

2.  It opens up the app. Ask questions like

    - "How many tickets are high priority"

    - "What is the average score from inspections?"

    - Show tickets grouped by status.

    and see that the output is generated from the Fabric data.

    ![](./media/image32.png)

## Exercise 7: Resources deployed

In this exercise, you will check the resources that are deployed as part
of the solution

### Fabric Resources

1.  Navigate to the Fabric workspace and look at the resources that are
    deployed.

    ![](./media/image33.png)

2.  Open the **Fabric Data agent** and chat with the agent.

    ![](./media/image34.png)

### Azure resources

1.  Open the Resource group rg-envtxxxxx.

    ![](./media/image35.png)

2.  Open the **Foundry project** and then select **Go to Foundry
    portal**.

    ![](./media/image36.png)
    
    ![](./media/image37.png)

3.  Switch on the **New Foundry toggle** and then select **Build** from
    the top menu.

    ![](./media/image38.png)

4.  Under **Agents**, you can see that there are 2 agents – **Chat** and
    **Title agent** created as part of the deployment.

    ![](./media/image39.png)

5.  Under the Knowledge section of the agent, you can see that the
    Foundry IQ is configured.

    ![](./media/image40.png)

## Summary

In this lab, you have understood how to design and build an AI solution
that is grounded in trusted business context rather than isolated
prompts or disconnected data sources. You gained practical exposure to
the architecture, workflows, and value of agentic intelligence built on
Microsoft’s unified data and AI ecosystem.
