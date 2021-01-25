# JiraSupport Extension for TestComplete
## About
You use the JiraSupport extension to create and update Jira issues and attach files to them directly from your TestComplete tests.
After you install the extension to TestComplete, you will get the [Jira](https://support.smartbear.com/testcomplete/docs/reference/program-objects/jira/index.html) object that has [methods](https://support.smartbear.com/testcomplete/docs/reference/program-objects/jira/methods.html) for creating and updating Jira issues.
## Requirements
- Atlassian Jira Server ver. 5.0 - 7.12 or Jira Cloud.
- To attach files to issues in Jira, their issue type must allow attachments.
## Installation
1. Download the **GitHub repository** to the computer where TestComplete is installed.
2. Double-click the **build.bat** file from the downloaded repository. It will create the installation file (**<GitHub repository>\out\JiraSupport.tcx**).
3. Double-click the **JiraSupport.tcx** file. This will invoke the [Installing Extension](https://support.smartbear.com/testcomplete/docs/working-with/extending/extensions-dialog.html?sbsearch=Installing%20Extension) dialog that displays the target installation folder.
Click **OK** to install the extension into TestComplete.
4. In TestComplete, select **File > Install Script Extensions** from the main menu. In the subsequent **Script Extensions** dialog, click **Reload** to update the list of available script extensions.
5. Select **Runtime Objects > Jira Object** to enable the installed extension: 
![The JiraSupport extension](/docs/jira-support-script-extension.png)

    Click **OK** to save the changes.
## Usage
```js
// JavaScript

// Create a Task item in Jira
function IssueToJira()
{
  // Log in to Jira
  Jira.Login("https://mycompany.atlassian/net", "John.Smith@mycompany.com", "c40Mwj3PovmZPFZbmIiwB8C6"); 
  // Create an object that defines task properties
  var jiraData = Jira.CreateNewIssueData("MyJiraProjectKey", "Task").
                         setField("summary", "This is a sample task summary").
                         setField("description", "Sample task description").
                         setField("customfield_10700", "Normal"); 
  // Post the issue to Jira
  var key = Jira.PostIssue(jiraData);
}
```
**Important:** To interact with Jira custom fields, use their identifiers instead of the field names. In the code above, it is `customfield_10700`.

To call this function from **keyword tests**, use the [Run Code Snippet](https://support.smartbear.com/testcomplete/docs/keyword-testing/reference/test-actions/run-code-snippet.html?sbsearch=Code%20Snippet%20Operation) operation.
## Methods
| **Method** | **Description** |
| ------ | ------ |
| [**Login**(*URL, Login, Password*)](https://support.smartbear.com/testcomplete/docs/reference/program-objects/jira/login.html) | Logs in to Jira.|
| [**CreateNewBugData**(*ProjectKey, Assignee, Priority, Summary, Description*)](https://support.smartbear.com/testcomplete/docs/reference/program-objects/jira/createnewbugdata.html) | Creates an object that has data for creating a Jira issue of the Bug type. |
| [**CreateNewIssueData**(*ProjectKey, IssueType*)](https://support.smartbear.com/testcomplete/docs/reference/program-objects/jira/createnewissuedata.html) | Creates an object that has data for creating a Jira issue of any type available in your Jira project. |
| [**PostIssue**(*NewIssueData*)](https://support.smartbear.com/testcomplete/docs/reference/program-objects/jira/postissue.html) | Creates a new issue in Jira. |
| [**CreateUpdateIssueData**()](https://support.smartbear.com/testcomplete/docs/reference/program-objects/jira/createupdateissuedata.html) | Creates an object that has data for updating a Jira issue. |
| [**UpdateIssue**(*IssueKey, UpdateIssueData*)](https://support.smartbear.com/testcomplete/docs/reference/program-objects/jira/updateissue.html) | Updates an existing issue in Jira. |
| [**PostAttachment**(*IssueKey, FileName*)](https://support.smartbear.com/testcomplete/docs/reference/program-objects/jira/postattachment.html) | Attaches a file to the specified Jira issue. |
## More Information
For complete information on using the extension and Jira integration, see the [TestComplete documentation](https://support.smartbear.com/testcomplete/docs/testing-with/log/working-with/creating-issue-reports/index.html).
