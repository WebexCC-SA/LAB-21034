---
#icon: material/folder-open-outline
icon: material/medal
---

# Mission 3: Configure Fulfillment Action and create a medication order using **Voice Flow**.

**<details><summary>What is a Fulfillment Action? <span style="color: orange;"></span></summary>**

Fulfillment Action is a task that an AI agent performs by understanding user intents and completing by connecting to external systems over an API.


## </details>

## Mission overview

In this Mission you will be using the Voice flow to execute the API call to create the medication order with a third party system.

![Profiles](../graphics/Lab1_AI_Agent/Fulfilment.png)

---

## Build

### Task 1. Configure Action in the AI Studio

1. Go to **Webex AI Agent Studio** Portal.

2. Select your AI agent with name **<copy><w class="attendee"></w>\_21209_AutoAI_Lab</copy>** that you created earlier and go to **Actions**. You will see one Action has already been created by default for the Agent Handover. We will now create one more action.
   ![Profiles](../graphics/Lab1_AI_Agent/2.17.png)

3. Click **Create New Action**. From the drop-down option, select **Fulfillment**.
   ![Profiles](../graphics/Lab1_AI_Agent/2.18.png)

4. Configure it with name **_<copy>Create_New_Order</copy>_** and the Action description below.<br>
   > Action description: **_<copy>Collect medication order details, delivery address or pickup preference, total price, and respond with the order ID number once the order is completed. The request will contain the order details. From the order details let the attendee know the order ID.</copy>_**
   ![Profiles](../graphics/Lab1_AI_Agent/2.18a.png)

5. Scroll down and click to create **New input entity**. Fill up the table with the following and then click on **Add**. <br>
   > Entity Name: **_<copy>address</copy>_** <br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Collect the attendee's delivery address — hotel name, room number.</copy>_**<br>
   > Example: **_<copy>Fairmont Austin or 101 Red River St, Austin, TX 78701</copy>_** <br>
   > Required: <b>Yes</b>
   ![Profiles](../graphics/Lab1_AI_Agent/2.19.png)

6. By following the same pattern, create an entity to collect the attendee's medication order details.<br>
   > Entity Name: **_<copy>orderDetails</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Collect the OTC medication information that the attendee orders. Make sure to do correct math. If one unit of ibuprofen is 8 dollars and the attendee would like to buy 2 units then the price should be 16 dollars. Don't use double quotes (") in the generated responses.</copy>_**<br>
   > Example: **_<copy>Ibuprofen 200mg (2 units) and Acetaminophen 500mg (1 unit)</copy>_**<br>
   > Required: <b>Yes</b>
   ![Profiles](../graphics/Lab1_AI_Agent/2.19.1.png)   

7. By following the same pattern, create an entity to store the total price information of the order.<br>
   > Entity Name: **_<copy>orderTotal</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>After the attendee confirms whether they need delivery or pickup, and confirms they would like to proceed with completing the order, collect the Total information and assign it to this slot. Always use the number for the total. For example use 24 $ but not twenty-four dollars.</copy>_**<br>
   > Example: **_<copy>24 dollars, 18 dollars</copy>_**<br>
   > Required: <b>Yes</b>
   ![Profiles](../graphics/Lab1_AI_Agent/2.19.2.png)  

8. By following the same pattern, create an entity to store the order status information.<br>
   > Entity Name: **_<copy>status</copy>_**<br>
   > Entity Type: <b>string</b> <br>
   > Description: **_<copy>Always create it as "new"</copy>_**<br>
   > Example: **_<copy>new</copy>_**<br>
   > Required: <b>Yes</b>
   ![Profiles](../graphics/Lab1_AI_Agent/2.19.3.png)  

9. At this point you should see 4 created entities. Please double-check that your configuration matches the screenshot below.
    ![Profiles](../graphics/Lab1_AI_Agent/2.61.png)

10. Scroll down and for the **Fulfillment** option select **Manage in the source flow (voice only)**. Click **Save**.
   ![Profiles](../graphics/Lab1_AI_Agent/19.2.1.png)

11. **Publish** your AI Agent.
   ![Profiles](../graphics/Lab1_AI_Agent/19.33.png)


12. Place a test call to the number that is related to your Entry Point. Ask to order OTC medication and provide the requested information. You should hear that the order was completed successfully. If not, use **Debugger** in the voice flow to troubleshoot.


<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>
