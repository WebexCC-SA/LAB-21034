---
#icon: material/folder-open-outline
icon: material/medal
---

# Mission 2: Integrating the AI Agent with Flow for Voice Calls

## Mission overview

Your mission is to:

Integrate the AI Agent with the Voice Flow.

### Task 1. Build WxCC voice flow with AI Agent.

1. Open [Collaboration Control Hub](https://admin.webex.com){:target="_blank"}, go to **Contact Center**, navigate to **Flows**, click the **Manage Flows** dropdown list, and select **Create Flows**.
   ![Profiles](../graphics/Lab1_AI_Agent/2.47.gif)

2. On the next page, select **Start from scratch** and click **Next**.
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.adf.png)

3. In the Voice Flow Designer, from the left side, move the **VirtualAgentV2** node and connect **Start Flow** to the **VirtualAgentV2** node.
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.ac.png)

4. Click **VirtualAgentV2**. In the **Contact Center AI Config**, select **Webex AI Agent (Autonomous)**. Under the **Virtual agent** config, select the AI Agent that you created in the previous mission — **<copy><w class="attendee"></w>_21034_Concierge</copy>**.
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.ad1.gif)

5. Add a **Disconnect Contact** node and connect the **Handled** output from the **VirtualAgentV2** node to the **Disconnect Contact** node.
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.ac1.png)

6. Add a **Queue Contact** node and connect the **Escalate** output from **VirtualAgentV2** to the **Queue Contact** node.
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.ae.gif)

7. Click **Queue Contact**. Select Channel type as **Voice**. Select the Queue as **<copy>21034_Queue</copy>**.
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.ae2.gif)

8. Add a **Play Music** node. Connect the **Queue Contact** node to the **Play Music** node. Loop the **Play Music** node to itself.
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.ae3.gif)

9. Click the **Play Music** node and select **defaultmusic_on_hold.wav** as the music file.
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.ae4.gif)

10. Validate and publish the flow with the **Latest** tag.
   ![Profiles](../graphics/Lab1_AI_Agent/2.48.ae5.gif)

11. Assign the flow to your **Entry Point**. First go to **Entry Point** and search for your channel **<copy><w class="attendee"></w>\_21034_Channel</copy>**.
   ![Profiles](../graphics/Lab1_AI_Agent/2.52.png)

12. Go back to Collaboration Control Hub > Contact Center. Click **Entry Points**. Click **<copy><w class="attendee"></w>\_21034_Channel</copy>**. In the **Entry Point** settings section, change the following and then **Save** the changes.<br/>
    Routing Flow: **<copy>MultiAgent_21034_<w class="attendee"></w></copy>**<br/>
    Version Label: **Latest**<br/>
    ![Profiles](../graphics/Lab1_AI_Agent/2.53.gif)

13. Dial the support number assigned to your **<w class="attendee"></w>\_21034_Channel** to test the Concierge AI Agent over a voice call.
   ![Profiles](../graphics/Lab1_AI_Agent/2.84.png)

<p style="text-align:center"><strong>Congratulations, you have officially completed this mission! 🎉🎉 </strong></p>
