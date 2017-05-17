## Introduction

These instructions are to help login into the Oracle Cloud Account. There is an assumption that:

- This is a brand new environment.
- The Developer Cloud Service has not been provided to you as part of the workshop.

### **STEP 1**: Login to your Oracle Cloud Account

- From any browser, go to the URL:
    `https://cloud.oracle.com`

- click **Sign In** in the upper right hand corner of the browser

    ![](images/100/Picture100-1.png)

- **IMPORTANT** - Under my services, select from the drop down list the correct data center and click on **My Services**. If you are unsure of the data center you should select, and this is an in-person training event, ***ask your instructor*** which **Region** to select from the drop down list. If you received your account through an Oracle Trial, your Trial confirmation email should provide a URL that will pre-select the region for you.

    ![](images/100/Picture100-2.png)

- Enter your identity domain and click **Go**.

    **NOTE:** The **Identity Domain, User Name** and **Password** values will be given to you by the instructor.

    ![](images/100/Picture100-3.png)

- Once your Identity Domain is set, enter your User Name and Password and click **Sign In**

  **NOTE:** For this lab you will assume the role of Project Manager ***Lisa Jones***. Although you are assuming the identify of Lisa Jones, you will log into the account using the **username** provided to you by your instructor, given to you by your corporation, or supplied to you as part of an Oracle Trial. As you progress through the workshop, you will remain logged in as a single user, but you will make “logical” changes from Lisa Jones the Project Manager to other personas.

    ![](images/lisa.png)

    ![](images/100/Picture100-3.5.png)

- You will be presented with a Dashboard displaying the various cloud services available to this account.

    ![](images/100/Picture100-4.png)

- If all your services are not visible, **click** on the **Customize Dashboard**, you can add services to the dashboard by clicking **Show.** For this workshop, you will want to ensure that you are showing at least the **Application Container, Developer and Storage** cloud services. If you do not want to see a specific service, click **Hide**

    ![](images/100/Picture100-5.png)

### **STEP 2**: Check/Set Storage Replication Policy

Depending on the state of your Cloud Account, you may need to set the replication policy, if it has not been previously set. In this step you will got to the Storage Cloud Service to check on the status of the Replicaton Policy. 

- Click on the **Storage** Cloud Service

    ![](images/100/Picture-01.png)

- If you see a message requesting that you **Set Replication Policy** as is shown below, click on the message. If the message is not displayed, your replicatin policy has already been set and you can continue to the next step by clicking on the **Dashboard** icon in the top right corner of the page.

    ![](images/100/Picture-02.png)

- Care must be taking when setting your replication policy, because it cannot be changed. With Trial accounts, the first option available will generatlly set the replication policy sufficient for this workshop, so we will take the Default, and click on the **Set** button. 

    ![](images/100/Picture-03.png)

- Click on the **Dashboard** button

    ![](images/100/Picture-04.png)

### **STEP 3**: Login to Developer Cloud Service

Oracle Developer Cloud Service provides a complete development platform that streamlines team development processes and automates software delivery. The integrated platform includes an issue tracking system, agile development dashboards, code versioning and review platform, continuous integration and delivery automation, as well as team collaboration features such as wikis and live activity stream. With a rich web based dashboard and integration with popular development tools, Oracle Developer Cloud Service helps deliver better applications faster.

- From the Cloud UI dashboard click on the **Developer** service. In our example, the Developer Cloud Service is named **developer99019**.

    ![](images/100/Picture100-6.png)

- The Service Details page gives you a quick glance of the service status overview.

    ![](images/100/Picture100-7.png)

- Click **Open Service Console** for the Oracle Developer Cloud Service. The Service Console will then list all projects for which you are currently a member.

    ![](images/100/Picture100-7.5.png)

Return to the Main Page to continue the labs [CloudNative100.md](CloudNative100.md)