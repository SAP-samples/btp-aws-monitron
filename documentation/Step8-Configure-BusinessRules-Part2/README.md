## Update and Activate SAP Business Rule Project
In this section, you will update decision table and activate business rule project.

### 1. Activate all objects in SAP Business Rule Project

1. In the SAP BTP cockpit, navigate to your subaccount and choose **Cloud Foundry** > **Spaces**.  Choose your space and then choose **action-management** application. Choose the url provided under **Application Routes** section.

    ![plot](./images/ActionManagementApplication.png)

2. Choose **Manage Business Rules** tile.

    ![plot](./images/ActionManagementHome.png)

3. Select **Events to Actions Rules Project** project and choose **Edit** and **Activate**.

    ![plot](./images/ActivateBusinessRulesProject.png)

4. Choose **Data Objects** tab. Select **EventInfo** and then choose **Edit**.

    ![plot](./images/DataObjects.png)

    Choose **Activate**.

    ![plot](./images/ActivateEventInfoDataObject.png)

5. Repeat above step for **ActionInfo** data object.

6. Choose **Rule Services** tab and select **DetermineAction** and then choose **Edit** and **Activate**..

    ![plot](./images/ActivateRuleServices.png)

7. Choose **Rules** tab and select **DecideAction** and then choose **Edit**.

    ![plot](./images/ActivateRules.png)

8. In the **Decision Table** section, go to **Action Id** column, type **fixed** in the field and select **Fixed Value** node. Click on the field as shown in the screenshot below.

    ![plot](./images/ActionIdInput.png)

9. Select **Create PM Notification** entry in the value help pop up.

    ![plot](./images/ActionIdValueHelp.png)

    Click on **save**. Again select the **DecideAction** and Choose **Edit** then Choose **Activate**

    ![plot](./images/SaveDecideActionRule.png)

10. Choose **Activate**.

    ![plot](./images/ActivateDecideActionRule.png)

11. Choose **Rulesets** tab and select **DetermineActionRuleSet** and then choose **Edit** and **Activate**.

    ![plot](./images/ActivateRuleSet.png)

12. Choose **Rule Services** tab and choose **Deploy**.

    ![plot](./images/DeployRuleServices.png)

13. Choose **Cloud Runtime** from the **Select a system to Deploy** list.

    ![plot](./images/SelectSystem.png)


    You will see a message **Your rule service is deployed successfully.** 

14. Select **MonitronActionConfigurations** Project project and choose **Edit** and **Activate**.

    ![plot](./images/ActivateMonitronProject.png)

15. Choose **Data Objects** tab. Select **EquipmentDetails** and then choose **Edit**.

    ![plot](./images/MonitronDataObjects.png)

    Choose **Activate**.

    ![plot](./images/ActivateEquipmentDetailsDataObject.png)

16. Repeat above step for **BucketInfo** data object, click on **Edit** and then Choose **Activate**

    ![plot](./images/BucketInfoDataObj.png)

17. Choose **Rule Services** tab and select **GetEquipmentDetails** and then choose **Edit** and **Activate**..

    ![plot](./images/ActivateMonitronRuleServices.png)

18. Choose **Rules** tab and select **FetchEquipmentDetails** and then choose **Edit** and **Activate**.

    ![plot](./images/ActivateMonitronRules.png)


19. Choose **Rulesets** tab and select **EquipmentDetailsRule** and then choose **Edit** and **Activate**.

    ![plot](./images/ActivateMonitronRuleSet.png)

20. Choose **Rule Services** tab and choose **Deploy**.

    ![plot](./images/DeployMonitronRuleServices.png)

21. Choose **Cloud Runtime** from the **Select a system to Deploy** list.

    ![plot](./images/MonitronSelectSystem.png)


    You will see a message **Your rule service is deployed successfully.**