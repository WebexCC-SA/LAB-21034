---
#icon: material/folder-open-outline
icon: material/medal
---

# Mission 1: Configure Transfer Action to the OTC Medication Order Agent

**<details><summary>What is a Transfer Action? <span style="color: orange;"></span></summary>**

Transfer Action is a task that an AI agent performs by understanding user intents and transferring the interaction back to the WxCC flow with custom data for further processing.

## </details>

## Mission overview

Your mission is to:

Configure a Transfer action on the **Concierge AI Agent** so that when the caller wants to order over-the-counter (OTC) medication, the call is transferred to the specialist agent **<copy><w class="attendee"></w>\_21034_OTC_Medication_Order</copy>**.

![Profiles](../graphics/Lab1_AI_Agent/TransferToFlow.png)

---

## Build

### Task 1. Create Transfer to flow action in AI Agent Studio portal

1. Go to **Webex AI Agent** Studio portal.

2. Open your Concierge AI agent with name **<copy><w class="attendee"></w>\_21034_Concierge</copy>** and then click on **Actions**.
   ![Profiles](../graphics/Lab1_AI_Agent/11.2.png)

3. Select **Add actions** option and create new **Transfer** action.
   ![Profiles](../graphics/Lab1_AI_Agent/11.3.gif)

4. Name the action as **<copy>Transfer_to_OTC_Medication_Order</copy>**.<br/> In the **Transfer condition** field, paste **<copy>When the customer wants to order OTC medication, transfer the call to the OTC Medication Order specialist agent</copy>**.
   ![Profiles](../graphics/Lab1_AI_Agent/11.4a.png)

5. Click on add **New input entity**. Configure it with the following: <br>
   > Entity name: **<copy>specialist</copy>**<br>
   > Entity type: **String**<br>
   > Entity description: **<copy>Collect if the customer wants to order OTC medication</copy>**<br>
   > Entity example: **<copy>OTC_Medication_Order</copy>**<br>
   ![Profiles](../graphics/Lab1_AI_Agent/11.5.png)

6. Finally, click on **Add** to add the new action.
   ![Profiles](../graphics/Lab1_AI_Agent/11.6.png)

7. **Publish** the AI Agent.
   ![Profiles](../graphics/Lab1_AI_Agent/11.14.png)

### Task 2. Configure voice flow to transfer callers to the OTC Medication Order agent

1. Open your Voice flow **<copy>MultiAgent_21034_<w class="attendee"></w></copy>**.
   ![Profiles](../graphics/Lab1_AI_Agent/11.7.gif)

2. Click on **Edit** to edit the flow.
   ![Profiles](../graphics/Lab1_AI_Agent/11.8.gif)

3. (<span style="color: red;"><strong>Read Only</strong></span>) In the previous task, we created an action with the **specialist** entity. The information about the value of the entity can be retrieved from the Activity Output Variable, specifically from **VirtualAgentV2XXXMetaData**.
   In the next steps, we will add the **Set Variable** block to see the MetaData in JSON format, and then you will add the **Parse** and **Case** nodes to handle the logic and send the call to the specialist agent **<copy><w class="attendee"></w>\_21034_OTC_Medication_Order</copy>**.
   ![Profiles](../graphics/Lab1_AI_Agent/11.11.png)

4. Create a new flow variable with name **<copy>MetaData_AI</copy>**. Select type as **string** and then click **Save**.
   ![Profiles](../graphics/Lab1_AI_Agent/11.9.gif)

5. Add **Set Variable** node to the flow and connect **Escalated** output of the **VirtualAgentV2** block to the **Set Variable** node.
   ![Profiles](../graphics/Lab1_AI_Agent/11.10.gif)

6. Click on **Set Variable** node, select Variable as **MetaData_AI**. For the Variable Value, first click on **VirtualAgentV2** block and copy the name of the MetaData Activity Output Variable. Then post this value inside of the {% raw %}{{ }}{% endraw %} to the Variable Value field.
   ![Profiles](../graphics/Lab1_AI_Agent/11.12.gif)

7. Connect **Set Variable** block to the **Queue** node for now. **Validate** and **Publish** the Flow.
   ![Profiles](../graphics/Lab1_AI_Agent/11.13.gif)

8. Place a test call to the number that is related to your Channel **<copy><w class="attendee"></w>\_21034_Channel</copy>**. During the conversation with the Concierge AI Agent **ask to order OTC medication**. The call should go to the only Queue that is currently configured in the flow.

9. After the call is completed, click on Debug and review the metadata in the Set Variable block.
   ![Profiles](../graphics/Lab1_AI_Agent/11.14.gif)

10. (<span style="color: red;"><strong>Read Only</strong></span>) From MetaData we can see the value of the specialist entity is "OTC_Medication_Order".
    ![Profiles](../graphics/Lab1_AI_Agent/11.15.png)

11. (<span style="color: red;"><strong>Read Only</strong></span>) To parse the value in the flow, we need to determine the JSON path to retrieve the value. By using an open-source tool (e.g. [JSONPath Online Evaluator](https://jsonpath.com/){:target="\_blank"}), you can ensure you are using the correct JSON path to extract the value you need. In our case, the JSON path is **$.actions.Transfer_to_OTC_Medication_Order[0].input.specialist** to retrieve the value for the specialist entity.
    ![Profiles](../graphics/Lab1_AI_Agent/11.16.png)

12. Move from the Debug to **Design** field. Create new flow **string** variable with name **<copy>specialist</copy>**.
    ![Profiles](../graphics/Lab1_AI_Agent/11.17.gif)

13. Add **Parse** block to the flow and connect **Set Variable** block to the **Parse** block.
    ![Profiles](../graphics/Lab1_AI_Agent/11.18.gif)

14. Configure the **Parse** block with the following:<br>

    > Input Variable: **<copy>MetaData_AI</copy>**<br>
    > Content Type: **<copy>JSON</copy>**<br>
    > Parse Variable: **<copy>specialist</copy>**<br>
    > Path Expression: **<copy>$.actions.Transfer_to_OTC_Medication_Order[0].input.specialist</copy>**<br>
    > ![Profiles](../graphics/Lab1_AI_Agent/11.19.png)

15. Add **Case** node to the flow and connect the **Parse** node to the **Case** node.
    ![Profiles](../graphics/Lab1_AI_Agent/11.20.gif)

16. Configure the **Case** node with the following:<br>

    > Variable: **<copy>specialist</copy>**<br>
    > LINK Description: **<copy>OTC_Medication_Order</copy>**<br>
    > ![Profiles](../graphics/Lab1_AI_Agent/11.21.png)

17. Bring a **Queue Contact** node to the flow. You will later connect this path to the specialist agent **<copy><w class="attendee"></w>\_21034_OTC_Medication_Order</copy>**.
    ![Profiles](../graphics/Lab1_AI_Agent/11.21.gif)

18. Configure the **Queue node** with **Voice** channel and **<copy>21034_Queue</copy>** as the queue.
    ![Profiles](../graphics/Lab1_AI_Agent/11.22.gif)

19. Connect **OTC_Medication_Order** output from **Case** node to the **Queue** node. Connect the **Queue** node to the **Play Music** node.
    ![Profiles](../graphics/Lab1_AI_Agent/11.23.gif)

20. Connect **Default** output from **Case** node to the **<copy>21034_Queue</copy>** Queue node.
    ![Profiles](../graphics/Lab1_AI_Agent/11.25.gif)

21. **Validate** and **Publish** the flow.
    ![Profiles](../graphics/Lab1_AI_Agent/11.26.gif)

22. Place a test call to the number that is related to your Channel **<copy><w class="attendee"></w>\_21034_Channel</copy>**. During the conversation with the Concierge AI Agent **ask to order OTC medication**. The call should park to a queue. After the call is completed, go to Debug, find the call to make sure it followed the OTC Medication Order path.
    ![Profiles](../graphics/Lab1_AI_Agent/11.27.png)

<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>
