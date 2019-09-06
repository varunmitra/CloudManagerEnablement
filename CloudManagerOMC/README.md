## Introduction to Cloud Manager

Cloud Manager, part of the Adobe Managed Cloud Services, enables organizations to self-manage Experience Manager in the cloud. It includes a continuous integration and continuous delivery (CI/CD) framework that lets IT teams and implementation partners expedite the delivery of customizations or updates without compromising performance or security.

Using the Cloud Manager self-service customer portal, Organizations can perform/leverage the following:

* Continuous Integration / Continuous Delivery of code to reduce time to market from months/weeks to days/hours.
* Code Inspection, performance testing and security validation based on best practices before pushing to production to minimize production disruptions.
* Automatic, scheduled or manual deployment even outside of business hours for maximum flexibility and control.
* Autoscaling feature intelligently detects the need for increased capacity and automatically brings online additional Dispatcher/Publish segment(s).

The following image illustrates the CI/CD process flow used in Cloud Manager:

![process flow](images/flow.png)


### Build and Run

Download the [Offline Marketing Cloud](OMC/omc-cloudmanager-master.zip).

Unzip the file and in a terminal/command window, navigate to the directory and run (in following order):

    $ npm install
    $ npm run build
    $ npm run serve
    $ open http://localhost:3000

### Getting Started

1. Access Offline Marketing Cloud by going to http://localhost:3000
2. Select `We.Retail Global` Card and Click on the Cloud Icon ![cloud icon](images/cloudIcon.png)

3. Click on Program Dropdown and click the Edit Button. ![Program Setup](images/EditProgram.jpeg)

4. You will see three options as General, KPI, and Provisioning tab.
5. In General tab, upload a thumbnail to your program. You can also add a relevant description to your program. ![Setup_Program-General](images/Setup_Program-General.png)

7. Under KPI, you can define your two KPIs (expectations for each deployment). Separate KPIs are defined for AEM Sites and AEM Assets. You will be able to specify the KPIs for the products you have licensed.
![Setup_Program-KPIs](images/Setup_Program-KPIs.png)

8. Under `Provisioning`, you can you can view or edit the provisioning configuration for production and non-production environments in your program. You will see `Autoscale is on`, if autoscaling has been turned on for the program.
![Setup_Program-Provisioning](images/Setup_Program-Provisioning.png)

### Environments
1. Cloud Manager `Overview` page has a summarized view of `Environments` and their `Status` which reflects their overall health.
```
Each Environment consists of:
1. Author
2. Publish
3. Dispatcher
Every Program has 1 Production Environment, 1 Stage Environment and can have multiple Development Environment
```
![environment](images/environmentsTab.png)

2. Click on Environment Card `Manage` Button or goto the `Environments` tab.

![manageEnv](images/manageEnv.png)

3. Verify the Environment Details i.e. Author, Publish and Dispatcher instance count, instance size, storage, region and status.
![envOverview](images/envOverview.png)

4. Click `Manage`
![envManage](images/envManage.png)

![envExpand](images/envExpand.png)

```
 You can manually expand AEM Publisher capacity by requesting additional segments
 ```

### Reports

1. Click `Reports`. 
![accessReports](images/accessReports.png)

2. Common Metrics are exposed through a Graphing Interface providing insights into status and health of instances

3. Switch `Environments` and `Instance` to view metrics for different Environment and Instances

![viewReports](images/viewReports.png)

### Configure Production CI/CD Pipeline

Once you have setup your program using Cloud Manager UI, you are ready to setup your pipeline.

Follow these steps to configure the behavior and preferences for your pipeline:
1. Verify the `Pipeline Settings` card in the `Overview` page

![pipelineSettings](images/pipelineSettings.png)

2. Edit `weretail-global` pipeline
3. Specify the `Branch` as `Master`
```
This can be any branch configured in Cloud Manager GIT Repository
```
![gitBranch](images/gitBranch.png)

4. Goto the `Environments` Tab.
```
You can configure how the code is getting deployed to Staging and ultimately, the Production environment.
```
![pipelineEnv](images/pipelineEnv.png)

5. Verify `Deployment Trigger`, `Important Failures Behavior`, `Testing` and `Dispatcher Configuration` for the Staging Environment
![stageConfig](images/stageConfig.png)

6. Verify `Deployment Options` and `Dispatcher Configuration` for the Production Environment
![prodConfig](images/prodConfig.png)

7. Goto `Testing` Tab and verify the different settings provided in `Sites Content Delivery/Distributed Load Weight` and `Assets Performance Testing Distribution`.

![pipelineTesting](images/pipelineTesting.png)

8. Click `Save`

### Deploy Your Program

Once you have configured your Pipeline (repository, environment, and testing environment), you are ready to deploy your code.
1. Click `Start New Deployment` from the Cloud Manager to start the deployment process.
![deploymentSetup](images/deploymentSetup.png)

2. The Pipeline Execution screen displays.
Click Build to start the process.
![buildProcess](images/buildProcess.png)

3. You will see an Execution Paused Dialog
![execPaused](images/execPaused.png)

4. Download Deployment Log, and Download Details
![summary](images/summary.png)

5. Click on `Review Summary`
6. Toggle `Override failed results` and `Submit`. Deployment should progress to `Stage Testing`.
![Overridefailedresults](images/Overridefailedresults.png)
7. You will see an `Execution Paused` message.
8. Click on `Review Summary`
9. Toggle `Override failed results` and `Submit`.
![Overridefailedresults](images/Overridefailedresults2.png)

10. Deployment will move onto `Performance Testing`
![performanceTesting](images/performanceTesting.png)

11. Execution will pause again.
12. Click on `Approved`
![prodApproval](images/prodApproval.png)

13. Deployment will move to `CSE Support`
![prodApproval](images/prodApproval.png)

14. Execution should auto finish.
![Executionfinished0](images/Executionfinished.png)

### Activity
1. Goto `Activity` Tab to view the Program Pipeline Actions.
![activity](images/activity.png)

2. Click on `Details` in the `Actions` column.
3. Review the summary for the latest pipeline activity
![activityDetails](images/activityDetails.png)

4. Click on the Notification button
![notifications](images/notifications.png)

****
Resources

[Cloud Manager Overview](https://helpx.adobe.com/experience-manager/kt/platform-repository/using/cloud-manager-feature-video-understand.html#CloudManagerOverview)

[Offline Marketing Cloud - Cloud Manager Edition](https://git.corp.adobe.com/jedelson/omc-cloudmanager)

[Introduction to Cloud Manager](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html)
