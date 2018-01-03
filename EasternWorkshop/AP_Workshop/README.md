# Building a Artificial Intelligent Conversational Bot

This repository serves as a tutorial to making a conversational AI bot, using Microsoft's Bot Framework.

Software bots are everywhere. You probably interact with them every day without realizing it. Bots, especially chat and messenger bots, are changing the way we interact with businesses, communities, and even each other. Thanks to light-speed advances in artificial intelligence (AI) and the ready availability of AI services, bots are not only becoming more advanced and personalized, but also more accessible to developers.

## Getting Started

In this workshop we will learn to do the following: 
1) Getting started with Source Control, GitHub 
2) Making a free Microsoft Azure Account 
2) Making a html, JavaScript, CSS file, and making an API call.
3) Saving everything to Github 
4) Testing the functionality on your website 


### Prerequisites

1) [Make an GitHub account](https://azure.microsoft.com/en-us/free/)
2) [Make an Azure account](https://azure.microsoft.com/en-us/free/)


## Exercises ##

This hands-on lab includes the following exercises:

- [Exercise 1: Create an Azure Bot Service](#Exercise1)
- [Exercise 2: Get started with Microsoft QnA Maker](#Exercise2)
- [Exercise 3: Expand the QnA Maker knowledge base](#Exercise3)
- [Exercise 4: Deploy the bot and set up continuous integration](#Exercise4)

## Exercise 1: Create an Azure Bot Service ##

The first step in creating a bot is to provide a location for the bot to be hosted, as well as configuring the services that the bot will use. [Azure Web Apps](https://azure.microsoft.com/services/app-service/web/) are perfect for hosting bot applications, and the Azure Bot Service is designed to provision and connect these services for you. In this exercise, you will create and configure an Azure Bot Service.

1. Open the [Azure Portal](https://portal.azure.com) in your browser. If you are asked to sign in, do so using your Microsoft account.

1. Click **+ New**, followed by **Intelligence + analytics** and then **Bot Service (preview)**.
 
    ![Creating a new Azure Bot Service](Images/portal-new-bot-service.png)

    _Creating a new Azure Bot Service_
  
1. Enter a name such as "qnafactbot" (without quotation marks) into the **App name** box. *This name must be unique within Azure, so make sure a green check mark appears next to it.* Make sure **Create new** is selected under **Resource Group** and enter the resource-group name "BotsResourceGroup" (again, without quotation marks). Then select the location nearest you and click **Create**. 

    ![Configuring a new Azure Bot Service](Images/portal-create-new-bot-service.png)

    _Configuring a new Azure Bot Service_
  
1. Click **Resource Groups** in the 
2.  on the left, followed by **BotsResourceGroup** to open the resource group created for the Bot Service.

    ![Opening the resource group](Images/portal-open-resource-group.png)

    _Opening the resource group_
  
1. Wait until "Deploying" changes to "Succeeded" indicating that the Bot Service was successfully deployed. You can click the **Refresh** button at the top of the blade to refresh the deployment status.

    ![Successful deployment](Images/portal-app-deployment-status.png)

    _Successful deployment_
  
1. Click **qnafactbot** (or the name you entered in Step 3) to open the App Service created for your bot.

    ![Opening the Bot Service](Images/portal-click-bot-service.png)

    _Opening the Bot Service_
  
1. Click **Create Microsoft App ID and password**. If you are asked to sign in again, do so using your Microsoft account.

    ![Creating an app ID and password](Images/portal-click-create-msft-app.png)

    _Creating an app ID and password_
  
1. Click **Generate an app password to continue**.

    ![Generating an app password](Images/portal-generate-password.png)

    _Generating an app password_
  
1. Copy the password to the clipboard. **You will not be able to retrieve this password after this step**, but will be required to use it in a later exercise. Once the password is saved, click **Ok** to dismiss the dialog.

    ![Copying the app password](Images/portal-new-password-generated.png)

    _Copying the app password_
  
1. Review the application registration information, and then click **Finish and go back to Bot Framework**.

    ![Finalizing the app registration](Images/portal-click-finish.png)

    _Finalizing the app registration_
  
1. Paste the password copied to the clipboard in Step 9 into the password box.

    ![Pasting the app password](Images/portal-paste-app-password.png)

    _Pasting the app password_
  
1. Click **NodeJS**. Then click **Question and Answer** and click **Create bot**. If you are asked to sign in again, do so using your Microsoft account. Also, if you are asked for permission for QnA Maker to access your info, click **Yes**.

    ![Selecting a language and template](Images/portal-select-template.png)

    _Selecting a language and template_

1. Check the **I agree** box, and then click **OK**. (If you are presented with the option of connecting to an existing knowledge base or creating a new one, choose the latter.) 

    ![Connecting to QnA Maker](Images/connect-bot-to-qnamaker.png)

    _Connecting to QnA Maker_
  
1. After a brief pause, the Bot Service will open in the portal and display the Bot Service editor, as pictured below. Behind the scenes, the bot has been registered, an Azure Web App has been created to host it, and the bot has been connected to Microsoft QnA Maker.

    ![The Bot Service editor](Images/portal-editor-new.png)

    _The Bot Service editor_  

1. To make sure these services can communicate with each other, you can test bot communication in the Azure Bot Service editor. To test, type the word "hi" (without quotation marks) into the chat window on the right side of the page. Then press **Enter** or click the paper-airplane icon.

    ![Testing bot communication](Images/portal-send-chat-test.png)

    _Testing bot communication_

1. Wait for the bot to respond with the word "hello," indicating your bot is configured and ready to go.

    ![Chatting with your bot](Images/portal-test-chat.png)

    _Chatting with your bot_

With the Bot Service deployed and configured, the next step is to update the Microsoft QnA Maker service that the bot is connected to.

<a name="Exercise2"></a>
## Exercise 2: Get started with Microsoft QnA Maker ##

[Microsoft QnA Maker](https://qnamaker.ai/) is part of [Microsoft Cognitive Services](https://www.microsoft.com/cognitive-services/), which is a suite of APIs for building intelligent apps. Rather than infuse a bot with intelligence by writing code that tries to anticipate every question a user might ask and provide a response, you can connect it to a knowledge base of questions and answers created with QnA Maker. A common usage scenario is to create a knowledge base from a FAQ so the bot can answer domain-specific questions such as "How do I find my Windows product key" or "Where can I download Visual Studio Code?"

In this exercise, you will use the QnA Maker portal to edit the knowledge base that was created when you connected the bot to QnA Maker. That knowledge base currently contains a single question and answer: "hi" and "hello." You will edit the response and then, in [Exercise 3](#Exercise3), populate the knowledge base with additional questions and answers.

1. Open the [Microsoft QnA Maker portal](https://qnamaker.ai/) in your browser. If you are not signed in, click **Sign in** in the upper-right corner and sign in with your Microsoft account. If you are presented with a terms agreement, check the **I agree** box and continue. 

    ![Signing in to QnA Maker](Images/qna-click-signin.png)

    _Signing in to QnA Maker_

1. Ensure that **My services** is selected at the top. Then click the pencil icon.
 
    ![Editing a QnA service](Images/qna-click-edit-icon.png)

    _Editing a QnA service_

1. Click **Settings**. Replace the value in the **Service name** box with "QnA Factbot" (without quotation marks). Then click **Save and retrain** to save the change. 
 
    ![Updating the service name](Images/qna-save-service-name.png)

    _Updating the service name_

1. Click **Knowledge Base**.
 
    ![Opening the Knowledge Base page](Images/qna-select-kb-tab.png)

    _Opening the Knowledge Base page_

1. Replace "hello" in the Answer column with "Welcome to the QnA Factbot!" Then click **Save and retrain** to save the change. 
 
    ![Updating a response](Images/qna-update-default-answer.png)

    _Updating a response_

1. Click **Test**.
 
    ![Opening the Test page](Images/qna-select-test-tab.png)

    _Opening the Test page_

1. Type "hi" into the box at the bottom of the chat window and press **Enter**. Confirm that the bot responds with "Welcome to the QnA Factbot!"
 
    ![Chatting with the bot](Images/qna-updated-chat-response.png)

    _Chatting with the bot_

This is a great start, but a simple reply to the greeting "hi" doesn't demonstrate a lot of value. To give your bot some meaningful content to work with, the next step is to populate the knowledge base with additional questions and answers.

<a name="Exercise3"></a>
## Exercise 3: Expand the QnA Maker knowledge base ##

You can enter questions and answers into a QnA Maker knowledge base manually, or you can import them from a variety of sources, including Web sites and local text files. In this exercise, you will use both of these techniques to populate the knowledge base with questions and answers and then publish the updated knowledge base for your bot to use.

1. Click **Settings** to the return to the Settings page in the [Microsoft QnA Maker portal](https://qnamaker.ai/).
 
    ![Opening the Settings page](Images/qna-select-settings-tab.png)

    _Opening the Settings page_

1. Paste the following URL into the **URLs** box:

	```
	https://traininglabservices.azurewebsites.net/help/faqs.html
	```

1. Click **Save and retrain** to populate the knowledge base with questions and answers from the Web site whose URL you provided.
 
    ![Importing questions and answers from a URL](Images/qna-add-faq-url.png)

    _Importing questions and answers from a URL_

1. Click **Knowledge Base** and confirm that six new questions and answers were added. Then click **Save and retrain** to save the changes.

    ![The updated knowledge base](Images/qna-updated-kb-01.png)

    _The updated knowledge base_

1. Click **Test** to return to the Test page. Type "What's the largest city in the world?" into the box at the bottom of the chat window and press **Enter**. Confirm that the bot responds as shown below.
 
    ![Testing the updated knowledge base](Images/qna-test-largest-city.png)

    _Testing the updated knowledge base_

1. The knowledge base only contains a few questions and answers, but can easily be updated to include more. You can even import questions and answers stored in text files on your computer. To demonstrate, click **Replace Knowledge Base** in the upper-left corner of the portal.
 
    ![Replacing the knowledge base](Images/qna-click-replace-kb.png)

    _Replacing the knowledge base_

1. Select the text file named **Final QnA.txt** included in the [resources that accompany this lab](https://a4r.blob.core.windows.net/public/bots-resources.zip). Click **OK** when prompted to confirm that importing this file will overwrite existing questions and answers.
 
1. Click **Knowledge Base** and confirm that 14 new questions and answers appear in the knowledge base. (The six you imported from the URL are still there, despite the fact that you were warned that they would be overwritten.) Then click **Save and retrain** to save the changes.

    ![The updated knowledge base](Images/qna-updated-kb-02.png)

    _The updated knowledge base_

1. Click **Test** to return to the Test page. Type "What book has sold the most copies?" into the box at the bottom of the chat window and press **Enter**. Confirm that the bot responds as shown below. 
 
    ![Chatting with the bot](Images/qna-test-book.png)

    _Chatting with the bot_

1. The knowledge base now contains 20 questions and answers, but an invalid character is present in the answer in row 7. To remove the character, click **Knowledge Base** to return to the Knowledge Base page. Locate the invalid character in row 7 between the words "most" and "Emmys," and replace it with a space character. Then click **Save and retrain**.
 
    ![Editing answer #7](Images/qna-invalid-char.png)

    _Editing answer #7_

1. Click **Publish** to publish the changes to the knowledge base.
 
    ![Publishing the knowledge base](Images/qna-click-publish.png)

    _Publishing the knowledge base_

1. Review the changes and click **Publish**. After a brief pause, you should be notified that the service has been deployed.
 
    ![Reviewing changes](Images/qna-review-publishing-changes.png)

    _Reviewing changes_

With a sample knowledge base deployed, it is now time to lend attention to the bot itself.

<a name="Exercise4"></a>
## Exercise 4: Deploy the bot and set up continuous integration ##

When you deployed a Bot Service in [Exercise 1](#Exercise1), an Azure Web App was created to host the bot. But the bot still needs to be written and deployed to the Azure Web app. In this exercise, you will code the bot using source code generated for you by QnA Maker. Then you will create a local Git repository for the code, connect it to the Azure Web App, and publish the bot to Azure, all using Visual Studio Code.

1. If you haven't installed Visual Studio Code, take a moment to do so now. You can download Visual Studio Code from http://code.visualstudio.com. You should also install [Node.js](https://nodejs.org) and [Git Client](https://git-scm.com/downloads) if they aren't already installed. All of these products work cross-platform and can be installed on Windows, macOS, or Linux.

	> An easy way to determine whether Node.js is installed is to open a terminal window or Command Prompt window and execute a **node -v** command. If the Node.js version number is displayed, then Node.js is installed.

1. Return to the Azure Portal and open the Bot Service you created in [Exercise 1](#Exercise1) if it isn't already open.

    ![Opening the Bot Service](Images/portal-click-bot-service.png)

    _Opening the Bot Service_
  
1. Click **Settings**, and then click **Configure**.

    ![Configuring continuous integration](Images/portal-expand-configure.png)

    _Configuring continuous integration_
  
1. Click the link to the zip file containing source code. Once the download is complete, unzip the zip file and copy its contents to the local folder of your choice.

    ![Downloading the source code](Images/portal-click-download-source.png)

    _Downloading the source code_
  
1. Scroll down the page and click the **Open** button to the right of "Advanced Settings."

    ![Opening advanced settings](Images/portal-open-advanced-settings.png)

    _Opening advanced settings_  

1. Click **Deployment credentials**.

    ![Viewing deployment credentials](Images/portal-select-deployment-credentials.png)

    _Viewing deployment credentials_  

1. Enter a user name such as "BotAdministrator" (you will probably have to enter a different user name since these must be unique within Azure) and enter "Password_1" as the password. Click **Save** to save your changes. Then close the blade by clicking the **x** in the upper-right corner.

    ![Entering deployment credentials](Images/portal-enter-ci-creds.png)

    _Entering deployment credentials_  

1. Click **Set up integration source**.
 
    ![Setting up an integration source](Images/portal-click-set-source.png)

    _Setting up an integration source_  

1. Click **Setup**, followed by **Choose Source**.
 
    ![Choosing a deployment source](Images/portal-select-source.png)

    _Choosing a deployment source_  

1. Select **Local Git Repository** as the deployment source, and then click **OK**. 
 
    ![Specifying a local Git repository as the deployment source](Images/portal-set-local-git.png)

    _Specifying a local Git repository as the deployment source_  

1. Start Visual Studio Code. Select **Open Folder** from the **File** menu and browse to the folder to which you copied the contents of the zip file downloaded in Step 4. Then select the "messages" folder and click **Select Folder**.
 
    ![Selecting the "messages" folder](Images/fe-select-messages-folder.png)

    _Selecting the "messages" folder_  

1. Click the **Git** button in the View Bar on the left side of Visual Studio Code, and then click **Initialize Git Repository**. This will initialize a local Git repository for the project.

    ![Initializing a local Git repository](Images/vs-init-git-repo.png)

    _Initializing a local Git repository_  

1. Type "First commit" into the message box, and then click the check mark to commit your changes.

    ![Committing changes to the local Git repository](Images/vs-first-git-commit.png)

    _Committing changes to the local Git repository_  

1. Use Visual Studio Code's **View -> Integrated Terminal** command to open an integrated terminal window. Execute the following command in the integrated terminal, replacing "BOT_APP_NAME" in two places with the name of the Bot Service you entered in [Exercise 1](#Exercise1), Step 3.

	```
	git remote add qnafactbot https://BOT_APP_NAME.scm.azurewebsites.net:443/BOT_APP_NAME.git
	```

1. Select **Command Palette** from the **View** menu to open Visual Studio Code's command palette. Then type "git pub" into the command palette and select **Git: Publish** to publish the bot code to Azure. 

    ![Publishing the bot](Images/vs-select-git-publish.png)

    _Publishing the bot_  

1. If prompted to confirm that you want to publish, click **Publish**.

    ![Confirming Git publishing](Images/vs-confirm-publish.png)

    _Confirming Git publishing_ 

1. If prompted for credentials, enter the user name and password ("Password_1") you specified in Step 7 of this exercise.

    ![Entering deployment credentials](Images/vs-enter-git-creds.png)

    _Entering deployment credentials_ 

1. Wait until your bot code has been published. A clock will appear over the Git button in the View Bar while publishing is in progress, and disappear when publishing is complete.

    ![The Git publishing indicator](Images/vs-git-delay-icon.png)

    _The Git publishing indicator_ 

In this exercise, you created a project for your bot in Visual Studio Code and set up continuous integration using Git to simplify publishing code changes. Your bot has been published to Azure and it's time to see it in action and learn how to debug it in Visual Studio Code.


## Authors

* **Adit Gupta** - *Initial work* - [AditGupta25](https://github.com/AditGupta25)


## Acknowledgments

https://github.com/MSFTImagine/computerscience