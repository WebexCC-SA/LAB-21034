---
#icon: material/folder-open-outline
icon: material/medal
---

# Mission 7: Configure Action with MCP

**<details><summary>What is MCP? <span style="color: orange;"></span></summary>**

MCP, or Model Context Protocol, is a standardized framework designed to facilitate the exchange of contextual information between AI models and external systems, enabling more dynamic and context-aware interactions. By using MCP, AI agents can be easily integrated with other external tools, allowing for different types of fulfillment.

## </details>

## Mission overview

In Mission 3, you configured fulfillment by adding an HTTP request node to your voice flow to create a medication order. Imagine that this HTTP request could be preconfigured on a server, and you simply need to connect your AI agent to that server to utilize it.</br>
</br>
Using an MCP (Model Context Protocol) server is a highly practical approach. If you manage multiple agents and need to configure various fulfillment options for them, you no longer need to rebuild the same logic repeatedly within your flows. Instead, you can simply connect an MCP server and select the specific tool you need. You will love it!</br>

For this mission, the MCP server was created and deployed on AWS with two tools:</br>
![Profiles](../graphics/Lab1_AI_Agent/MCPAction_.png)</br>
1) Check Pharmacy and Clinic Locations. The addresses are stored on the MCP server itself.</br>
2) Check the medication order status by sending API call with the order ID to the MockAPI repository.</br>

This MCP Server repository you can find on GitHub below. In the **READMe.md** file you will be able to find instructions on how to deploy it on AWS. You can use it as the example for implementing the MCP server for your production tenant, but for this lab it is already deployed so the link below is just the reference of the source code.</br>
</br>
**<copy>https://github.com/mdanylch/event_health_mcp_21034</copy>**

In this mission you will work on adding this External MCP server to Webex cloud and plug it in with your AI Agent.

![Profiles](../graphics/Lab1_AI_Agent/MCPAction.png)

---

## Build

### Task 1. Create Agentic App in Webex Developer Portal.

1. Open [Webex Developer Portal](https://developer.webex.com/){:target="_blank"} .

2. Click on **Login**. Login with your admin credentials.
![Profiles](../graphics/Lab1_AI_Agent/15.1.png)

3. Under the Profile, click on **My Webex App**
![Profiles](../graphics/Lab1_AI_Agent/15.2.png)

4. Click on **Create a New App**.
![Profiles](../graphics/Lab1_AI_Agent/15.3.png)

5. On the next page, select **Create an Agentic App**.
![Profiles](../graphics/Lab1_AI_Agent/15.4.png)

6. Name your app as **<copy><w class="attendee"></w>\_MCP_Server</copy>**
![Profiles](../graphics/Lab1_AI_Agent/15.5.png)

7. For **Agent App Description**, paste the text below (use the **copy** icon on the code block):

    ``` text
    This MCP server is used for the following:

    1) Check pharmacy and partner clinic locations near the event venue
    2) Check medication order status based on the order ID.
    ```
![Profiles](../graphics/Lab1_AI_Agent/15.6.png)

8. Select an available Agentic App Icon. Click 2 times on an Icon.
![Profiles](../graphics/Lab1_AI_Agent/15.7.gif)

9. For the Agentic App URL enter **<copy>https://y4drgmvgpb.us-east-1.awsapprunner.com/mcp</copy>** and for Agentic App auth type select **Custom Headers**. Finally click on **Add Agentic App**.
![Profiles](../graphics/Lab1_AI_Agent/15.8.png)

### Task 2. Enable the Agentic App in Control Hub.

1. Go to Control Hub. If you are under the Contact Center settings, click on **Main Menu**.
![Profiles](../graphics/Lab1_AI_Agent/15.9_.png)

2. Open **Apps**, then click on **Agentic Apps**.
![Profiles](../graphics/Lab1_AI_Agent/15.9.png)

3. In the Apps find your Server name that is associated to your id **<copy><w class="attendee"></w>\_MCP_Server</copy>** and open it.

4. Make it **Allowed for all users** and enable the **Authorize automatic server data updates**. Click **Save**.
![Profiles](../graphics/Lab1_AI_Agent/15.10a.png)

5. Click on **Authentication**. Configure the custom header with **Key 1**: **<copy>MCP_REQUEST_HEADERS</copy>** and the **Value** **<copy>4f9a2b7e1d8c6b3a0f92e4d5c6b8a1f7</copy>**. Then click on **Save**.
![Profiles](../graphics/Lab1_AI_Agent/15.11.png)

6. Click on **Tools** and Allow **get_pharmacy_locations** and **check_order_status** tools and **Allow signature change**. Click **Save**.
![Profiles](../graphics/Lab1_AI_Agent/15.12.png)

### Task 3. Configure the MCP Server tools with your AI agent.

1. Open up your AI Agent and go to **Actions**, click on **Add action**, click on **Select available**.
![Profiles](../graphics/Lab1_AI_Agent/15.13.png)

2. Add the tools that are associated to your Agentic App name, and click on **Add**.
![Profiles](../graphics/Lab1_AI_Agent/15.14.png)

3. **Publish** the changes.
![Profiles](../graphics/Lab1_AI_Agent/15.15.png)

4. Place a test call. First ask for the nearest pharmacy or clinic location, and then ask to trace the medication order that you created earlier based on the order ID.

5. You can also test the MCP connections from the **Chat or Voice Preview**.
![Profiles](../graphics/Lab1_AI_Agent/15.16.png)

<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>
