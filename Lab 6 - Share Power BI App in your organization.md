![Microsoft Power Platform.](Images/powerbi-welcome-6.png 'Microsoft Power Platform')

# Lab 6 - Share Power BI App in your Organization

**Contents** 

<!-- TOC -->

- [Introduction](#introduction)
- [Power BI – Share a Report](#power-bi-share-a-report)
  - [Power BI – Link settings](#power-bi-link-settings)
  - [Power BI – Manage Permissions to a Report](#power-bi-manage-permissions-to-a-report)
- [Power BI – Share a Dashboard](#power-bi-share-a-dashboard)
  - [Power BI – Manage Permissions to a Dashboard](#power-bi-manage-permissions-to-a-dashboard)
- [References](#references)

## Introduction

**Sharing** is the easiest way to give people access to your reports and dashboards in the Power BI service. You can share with people inside or outside your organization.

When you share a report or dashboard, the people you share it with can view it and interact with it but can't edit it. They see the same data that you see in the reports and dashboards and get access to the entire underlying dataset unless row-level security (RLS) is applied to the underlying dataset. The coworkers you share with can reshare with their coworkers if you allow them to.

   ![](Images/powerbi-06-01.png)

The Power BI service offers other ways to collaborate and distribute reports and dashboards, too. Read [Ways to collaborate and share in Power BI](https://docs.microsoft.com/en-us/power-bi/collaborate-share/service-how-to-collaborate-distribute-dashboards-reports) to see which way works best for your circumstances.

Where you can share:

- You can share reports and dashboards from My Workspace.
- You can share from workspaces other than My Workspace, if you have the Admin or Member role in the workspace. If you have the Contributor or Viewer role, you can share if you have Reshare permissions.
- You can share from the Power BI mobile apps.
- You can't share directly from Power BI Desktop. You publish reports from Power BI Desktop to the Power BI service.

## Power BI – Share a Report

1. In a list of reports, or in an open report, select **Share** ![](Images/powerbi-06-02.png) .

2. Then in the **Send link** dialog, you'll see the option to copy the sharing link or share it via Outlook and Teams to **People in your organization**

   ![](Images/powerbi-06-03.png)

>**Note**: Your organization may not allow you to create shareable links to **People in your organization**. Learn more about this **tenant setting** in the admin portal documentation.

3. Selecting **Copy link** will automatically generate and copy a shareable link to your clipboard.

   ![](Images/powerbi-06-04.png)

4. You can also choose to directly send the link to **Specific people** or groups (distribution groups or security groups). Just enter their name or email address, optionally type a message, and select **Send**.

   ![](Images/powerbi-06-05.png)

5. After you select **Send**, Power BI sends the link via email to your recipients.

   ![](Images/powerbi-06-06.png)

6. When your recipients receive the email, they can select **Open this report** and automatically get access to the report through the shareable link.

   ![](Images/powerbi-06-07.png)

### Power BI – Link settings

You can choose who your sharing link gives access to and what they can do with the report and associated data:

   ![](Images/powerbi-06-08.png)

- **People in your organization**

  This type of link can allow people in your organization to access the report. This link will not work for external users nor guest users. Use this link when you want to share with someone in your organization and are comfortable with them passing the link around to other people inside your organization, but when you want to ensure that the link won’t work for external nor guest users.
  
- **People with existing access**

  This type of link generates a URL to the report, but it does not give any access to the report. Use this if you just want to send a link to somebody who already has access.

- **Specific people**

  This type of link allows specific people or groups to access the report. If you select this option, enter the names or email addresses of the people you wish to share with. With this link type you can share to guest users in your organization’s Azure Active Directory (AAD), but you cannot share to external users who are not guests in your organization.

### Settings

Links that give access to **People in your organization** or **Specific people** will always include at least read access. However, you can also specify if you want the link to include or exclude the following permissions as well:

- Reshare permissions (included by default) – allows recipients to share the report to others
- Build permissions (excluded by default) – allows recipients to build their own reports in other workspaces based on the data associated with the report. Read more about [creating reports based on datasets from different workspaces](https://docs.microsoft.com/en-us/power-bi/connect-data/service-datasets-discover-across-workspaces).

Links for **People with existing access** do not have any additional settings because these links do not give any access to the report.

### Additional considerations

1. If a user tries to access a report using a link that they don't have access to, they can only access the report if there is another link granting them access or they have direct access to the report.

2. If your tenant admin has disabled shareable links to **People in your organization**, you can only copy and share links to **Specific people** or **People with existing access**.

3. If you have reshare permissions to the report but, you do not have reshare permissions to the report’s underlying data, your shareable links will not give access to the underlying data.

4. If you don't have reshare permissions to the report, you can only copy and share links to **People with existing access**.

5. Additionally, if you don't have a Power BI Pro License, you can only copy and share links to **People with existing access**.

## Power BI – Manage Permissions to a Report

1. To manage permission and manage links that give access to the report, select **More options (...)** in the upper right of the sharing dialog, and then select **Manage permissions**.

   ![](Images/powerbi-06-09.png)

2. This will launch the **Manage permissions** pane where you can copy or modify existing links or grant users direct access. To modify a given link, select **More options (...)**.

   ![](Images/powerbi-06-10.png)

3. To grant users direct access to the report select the plus icon (+), enter their name or email address, optionally type a message, and select **Grant access**.

   ![](Images/powerbi-06-11.png)

4. For additional access management capabilities, select the **Advanced** option in the footer of the **Manage permissions** pane. This takes you to the management page, where you can:

- View, manage, and create **Links**.
- View and manage who has **Direct access** and grant people direct access.
- View and manage **Pending** access requests and invitations.
- View and manage **Related content**.
- Apply **Filters** or **Search** for specific links or people.

  ![](Images/powerbi-06-12.png)

>**Note**: Each report cannot have more than 1,000 sharing links. In the unlikely case that your report hits this max limit, we recommend removing links that give **Specific people** access and instead grant those users direct access.

## Power BI – Share a Dashboard


