---
#icon: material/folder-open-outline
icon: material/medal
---

# Mission 2: Integrating the AI Agent with Flow for Voice Calls

## Mission overview

Your mission is to:

Integrate the AI Agent with the Voice Flow.

### Task 1. Build WxCC voice flow with AI Agent.

1. Open [Control Hub](https://admin.webex.com){:target="_blank"} and go to **Contact Center** navigate to **Flows**, click on **Manage Flows** dropdown list and select **Create Flows**.
   ![Profiles](../graphics/Lab1_AI_Agent/2.47.gif)

2. On the next page, search for the flow that is related to your ID **<copy>AutonomousAI_Flow_21209_<w class="attendee"></w></copy>**. Open the flow by clicking on it.
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.ab.png)

3. Click on **Edit** to start editing the flow.
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.ac.png)

4. Click on **VirtualAgentV2** node and change the Virtual Agent name to the one that is related to your ID - **<copy><w class="attendee"></w>_21209_AutoAI_Lab</copy>**.
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.ad.gif)

5. Validate and publish the flow. 
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.ae.gif)

6. Assign the Flow to your **Entry Point**. Do this by first going to **Entry Point** and search for your channel **<copy><w class="attendee"></w>\_21209_Channel</copy>**.
   ![Profiles](../graphics/Lab1_AI_Agent/2.52.png)

7. Click on **<copy><w class="attendee"></w>\_21209_Channel</copy>**. In the **Entry Point** settings section, change the following and then **Save** the changes.<br/>
    Routing Flow: **<copy>AutonomousAI_Flow_21209_<w class="attendee"></w></copy>**<br/>
    Version Label: **Latest**<br/>
    ![Profiles](../graphics/Lab1_AI_Agent/2.53.gif)
8. Dial the support number assigned to your **<w class="attendee"></w>\_21209_Channel** to test the Autonomous AI Agent over a voice call.
   ![Profiles](../graphics/Lab1_AI_Agent/2.84.png)

<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>
