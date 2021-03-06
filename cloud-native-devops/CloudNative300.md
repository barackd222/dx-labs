## Introduction

This is the third of several labs that are part of the **Developer Experience workshop.** This workshop will walk you through the Software DevelopLifecycle (SDLC) for a Cloud Native project that will create and use several Microservices.

In the previous lab 1.2, the Java Developer created several microservices that pull data from twitter and allow for dynamic filtering based on keywords. In this lab, you will assume the role of a front-end JavaScript developer who will create a web application that incorporates the data from those microservices. This node.js application will be developed in the Developer Cloud Service taking advantage of automated builds and deployments to the Application Container Cloud Service.

## Objectives

- Access Developer Cloud Service
- Import Code from external Git Repository
- Import Project into Brackets
- Build and Deploy project using Developer Cloud Service and Oracle Application Container Cloud Service

## Required Artifacts

- The following lab requires an Oracle Cloud account that will be supplied by your instructor. You will need to download and install latest version of the Brackets text editor. The following instructions are provided to help with the instruction of Brackets and Git. If you have your own preferred IDE and / or you are comfortable with Git, you are welcome to use your own tools. 

+ [Install Local Environment - Brackets and Git](Brackets.md)

# Create Initial Twitter Marketing UI Service

### **This section of the lab is executed by the Javascript Developer Persona**

## Create Initial Git Repository

### **STEP 2**: Create Initial Git Repository

As in the previous lab, we could start coding this application from scratch at this point. However, one of our colleagues has already begun working on the shell for our web application outside of the Developer Cloud Service. We want to use his work as a starting point and extend it to incorporate our twitter microservices. To pull his code into the Developer Cloud Service, we will clone his external GIT repository.

- Click on **Project** on the navigation panel.

- Click on **New Repository** to create a new Git Repository

    ![](images/300/image017.png)  

- In the New Repository wizard enter the following information and click **Create**.

    **Name:** `TwitterMarketingUIMicroservice`

    **Description:** `Twitter Marketing UI Microservice`

    **Initial content:** Import existing repository and enter the URL: `https://github.com/pcdavies/JETTwitterQuickStart.git`

    ![](images/300/image018.5.png)  

- You have now created a new GIT repository based on an existing repository.

    ![](images/300/image019.png)  

## Create Default Build and Deployment Process

### **STEP 3**: Create Default Build Process

Now that we have the source code in our managed GIT repository, we need to create a build process that will be triggered whenever a commit is made to the master branch. We will set up a shell script build process in this section.

- Click **Build** on the navigation panel to access the build page and click **New Job**.

    ![](images/300/image020.png)  

- In the New Job popup enter `Twitter Marketing UI Build` for Job Name and click **Save**.

    ![](images/300/image021.png)  

- You are now placed into the job configuration screen.

    ![](images/300/image022.png)  

- Click the **Source Control** tab. Click Git and select **TwitterMarketingUIMicroservice.git** from the URL drop down.

    **Note:** Make sure you select the Git repository for the Twitter Marketing UI Microservice.

    ![](images/300/image023.png)  

- Click the **Triggers** tab.  Select Based on **SCM polling schedule**.

    ![](images/300/image024.png)  

- Click the **Build Steps** tab. Click **Add Build Step**, and select **Execute shell**.

    ![](images/300/image025.png)  

- For **Command** enter: `npm install`

    ![](images/300/image026.png)  

- Click the **Post Build** tab. Check **Archive the artifacts** and enter `**/target/*` for Files to Archive.  Verify **GZIP** in the Compression Type.

    ![](images/300/image027.png)  

- Click **Save** to complete the configuration. A build should start automatically within a minute or two.  If it does not start automatically, click on the **Build Now** button. The status will change to the following:

    ![](images/300/image028.png)  

- Once the build begins, it should take about approximately 1 to 2 minutes for the build to complete. Wait for the build to complete before continuing on to the next step, as we need the build artifact to create the deployment configuration.

    ![](images/300/image029.png)  

### **STEP 4**: Create Default Deployment Process

Now that we have an automated build process, we will set up a deployment configuration that will push our build artifacts to a node.js environment running on the Application Container Cloud Service whenever a successful build occurs.

- Click **Deploy** to access the Deployment page and click **New Configuration**.

    ![](images/300/image030.png)  

- Enter the following data:

    **Configuration Name:** `TwitterMarketingUIDeploy`

    **Application Name:** `JETFrontEndApp`

    ![](images/300/image031.png)  

- Right of Deployment Target click **New** and select **Application Container Cloud**

    ![](images/300/image032.png)  

- Enter the following data and click Test Connection. If Successful click Use Connection

    **Data Center**: `<Your Assigned Datacenter>` ***(Ask instructor if needed)***

    **Identity Domain**: `<Your Identity Domain>`

    **Username**: `<Your User Name>`

    **Password**: `<Supplied Password>`

    ![](images/300/image033.2.png)  

- Set ACCS Properties to Runtime **Node** and Subscription **Hourly**. 
- Click Type **Automatic**. 
- Select Job **Twitter Marketing UI** Build.
- Select **target/jet-quickstart-client-dist.zip** for Artifact.

    ![](images/300/image034.png)  

- Click **Save**

    ![](images/300/image035.png)  

- Click the gear drop down and select **Start**

    ![](images/300/image036.png)  

- Wait until the message **Starting application** changes to **Last deployment succeeded**

    ![](images/300/image037.png)  

### **STEP 5**: Login to Oracle Application Container Cloud Service

- Navigate back to the Oracle Public Cloud tab. Click **Dashboard** to return back to main Cloud Service Dashboard.

    ![](images/300/image042.2.png)  

- On the Application Container Cloud Service (ACCS) click ![](images/300/image043.png)  and select **Open Service Console**

    ![](images/300/image044.png)  

- On the ACCS Service Console you can view all the deployed applications including our newly create **JETFrontEndApp**.

    ![](images/300/image045.png)  

- Click on URL or copy and paste the URL into the address bar of a new tab to bring up the application.

    ![](images/300/image046.png)  

# Extend default application to Display Twitter Feed

Now that we have our default application we want to extend this application to add the display of the twitter feed. For this task we will use Brackets text editor to pull down the code from Developer Cloud Service and add in our modifications. Once the new code is ready for deployment we will check the code in on a branch so that it can go through a code review prior to build and deployment.

## Clone Project to Brackets Text Editor

### **STEP 6**:	Start Brackets Text Editor

- In Windows Explorer, create a new directory (this is where the code will be downloaded to)

- Start **Brackets** text editor. How you start Brackets will depend on your OS.

- Click on the `File` menu and click `Open Folder`. Select the newly created directory.

    ![](images/300/brackets-newfolder-001.png)

### **STEP 7**: Copy GIT URL

- Back in Developer Cloud Service, click on **Project**. On right side, select the URL for **TwitterMarketingUIMicroservice.git**. Right click and select **Copy**

    ![](images/300/image054.2.png)  

### **STEP 8**: Clone GIT Repository

- Back in the Brackets editor, Click on ![](images/300/image055.png) GIT icon found on the right side of the editor.

  ![](images/300/image055.5.png)  

- Click **Clone**

  ![](images/300/image056.png)  

- Paste in Git URL that you captured from Developer Cloud Service. Username should be populated automatically. Enter your **Password** and click **Save credentials**. Once completed click **OK** to start the cloning process.

    ![](images/300/image057.png)  

- While the clone is running a dialog box will show you the progress.

    ![](images/300/image058.png)  

- You now have a local copy of the repository.

    ![](images/300/image059.png)  

### **STEP 9**: Run Live Preview.

- Before we make our code changes lets first run the code locally.

- Expand **doc_root** and select **index.html**

    ![](images/300/image060.png)  

- On right hand panel, click ![](images/300/image061.png) Live Preview. This will start your JavaScript application in a browser. Once you verify the application is working you can close the browser.

![](images/300/image062.png)  

## Add Code to display Twitter Feed in Table Format

### **STEP 10**:	Modify graphics.html

- Expand **doc_root -> js -> views** and click **graphics.html**.

    ![](images/300/image063.png)  

- Replace the existing code with the code block below:

```
<h1>Graphics Content</h1>

<table id="table" summary="Tweet List" data-bind="ojComponent:{component:'ojTable',
        data: tweets,
        columns: [
               {headerText: 'User Name', field: 'User', id: 'name', sortable: 'enabled'},
               {headerText: 'User Location', field: 'Location', id: 'location', sortable: 'enabled'},
               {headerText: 'Source', field: 'Source', id: 'source', sortable: 'enabled'},
               {headerText: 'Tweet', field: 'Text', id: 'text'}
               ],
        rootAttributes: {'style':'width: 100%; height:100%;'},
        scrollPolicy: 'loadMoreOnScroll',
        scrollPolicyOptions: {'fetchSize': 10}}">
</table>
```

![](images/300/image064.png)  

### **STEP 11**: Modify graphics.js

- Expand **doc_root -> js -> viewModels** and click **graphics.js**.

    ![](images/300/image065.png)  

- Add the code block below to the bottom on the **graphics.js** file:

```
/*global $, define, console*/
/*jslint sloppy:true*/

define(['ojs/ojcore', 'knockout', 'ojs/ojtable'], function (oj, ko) {

    function mainContentViewModel() {

        // change this root variable to point to YOUR environment
        var root = 'https://javatwittermicroservice-metcsgse00210.apaas.em2.oraclecloud.com/',
            self = this,
            uri = 'statictweets/',
            prettySource = function (source) {
                return source.substring(source.indexOf('>') + 1, source.lastIndexOf('<'));
            },
            url = root + uri;

        self.items = ko.observableArray([]);
        self.tweets = new oj.ArrayTableDataSource(self.items, {
            idAttribute: 'Id'
        });

        $.ajax({
            url: url,
            method: 'GET'
        }).success(function (result) {
            console.log(result.tweets);
            var items = self.items();
            ko.utils.arrayForEach(result.tweets, function (value) {
                // make sure this is a creation tweet
                if (!!value.user) {
                    items.push({
                        Id: value.id,
                        Location: value.user.location,
                        Text: value.text,
                        Source: prettySource(value.source),
                        User: value.user.name
                    });
                }
            });
            self.items.valueHasMutated();
        });
    }
    return mainContentViewModel;
});
```

- Back in the browser; navigate back to the Application Container Cloud Service service console. Copy URL for **JavaTwitterMicroservice** that was created in Lab 200.

    ![](images/300/image066.png)  

- Replace the existing URL with your URL for the **root variable**. ***Make sure*** there is a '`/`' (front slash) at the **end of the URL**.

    ![](images/300/image067.png)  

- Completed graphics should look something like the image below:

    ![](images/300/image068.png)  

- Save all files by clicking **File -> Save All**

![](images/300/image069.png)  

### **STEP 12**: Test new changes

- Click ![](images/300/image070.png) Live Preview to test out the new changes.

- Click ![](images/300/image071.png) and select **Graphics**

    ![](images/300/image072.png)

- In the graphics sections you can now see all the twitter feed data:

    ![](images/300/image073.png)

# Create a new Branch and Commit Code

### **This section of the lab is executed by the Javascript Developer Persona**

## Create a Branch and Commit Code

### **STEP 13**: Create a new Branch and Commit Code

- First we need to create a new branch to check in all of our changes for this feature. In the left hand navigation panel, select **master** and click **Create new branch**.

    ![](images/300/image074.png)

- In popup window, **enter** `Feature4` for branch name and click **OK**.

    ![](images/300/image075.png)

- Click  Git ![](images/300/image076.png) icon. Check the box next to **Commit** to select all modified files.

    ![](images/300/image077.png)

- Click **Commit**.

- In popup enter the **comment** `Added code to display twitter feed in table format` and click **OK**. This will commit the changes to your local Git repository.

    ![](images/300/image078.png)

- Click ![](images/300/image079.png) Git Push icon.

- In popup window leave all defaults and click **OK**

    ![](images/300/image080.png)

- Once Git Push completes click **OK**.

    ![](images/300/image081.png)

# Initiate Merge Process

### **This section of the lab is executed by the Javascript Developer Persona**

## Create Merge Request

### **STEP 14**: Review Sprint Status and create Merge Request

- Click on the **Code** tab, select the **Feature4** branch and then click on the **Commits** sub tab. Now view the recent commit that we made to branch from Brackets.

    ![](images/300/image084.png)

- Now that "John Dunbar" has completed the task of displaying twitter feed in table format, a Merge Request can be created by John and assigned to "Lisa Jones." 

    ![](images/300/image084.5.png)

- Click on **Merge Requests**, and then click on the **New Merge Request button**.

    ![](images/300/image085.png)

- Enter the following information into the New Merge Request and click **Next**

    **Repository:** `TwitterMarketingUIMicroservice.git`

    **Target Branch:** `master`

    **Review Branch:** `Feature4`

    ![](images/300/image086.png)

- Enter the following information into Details and click **Create**

    **Summary:** `Merge Feature 4 into master`

    **Reviewers:** `<Your Username>`

    ![](images/300/image087.5.png)

- In the **Write** box, enter the following comment and then click on the **Comment** button to save

    **Comment:** `I added table of Twitter feed to graphics tab`

    ![](images/300/image088.png)

# Manage Merge Process (as Project Manager Persona)

### **This section of the lab is executed by the Project Manager Persona**

## Merge the Branch

### **STEP 15**: Merge Requests

- In the following steps the Project Manager Persona will merge the branch created by the Javascript Developer into the master.

- Click on **Merge Requests**. Select the **Assigned to Me** search. After the search completes, click on the **Merge Feature 4 into master** assigned request.

    ![](images/300/image094.png)

- Once the request has loaded, select the **Changed Files tab**. As the persona Lisa, you will now have the opportunity to review the changes in the branch, make comments, request more information, etc. before Approving, Rejecting or Merging the Branch.

    ![](images/300/image095.2.png)

- Click on the **Merge** button.

    ![](images/300/image096.png)

- Leave the defaults, and click on the **Merge** button in the confirmation dialog.

    ![](images/300/image097.png)

- Now that the code has been committed to the Developer Cloud Service repository, the build and deployment will automatically start. Click on **Build**, and you should see a **Twitter Marketing UI Build** in the Queue

    ![](images/300/image098.png)

- Wait a minute or two for the build to complete. The **Last Success** will be set to **Just Now** when the build completes.

    ![](images/300/image099.png)

- Click on Deploy. Wait for the **Deploy** Status to change to **Deployment update in progress**, and then change to **Last deployment succeeded** – **Just now**.

    ![](images/300/image100.png)

# Test the Change

## Test the JETFrontEndAPP UI in the Cloud

### **STEP 16**: Test the Front End

- Once the service has successfully deployed, click on the **JETFrontEndApp** link

    ![](images/300/image101.png)

- When the new browser tab loads, click **Graphics** to display twitter feed data.

    ![](images/300/image102.png)

- You are now ready to move to the next lab.

Return to [Lab 1.5](CloudNative400.md) to continue the labs.