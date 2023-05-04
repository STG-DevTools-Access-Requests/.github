# DevTools Access Requests

## Getting Started

## Implementation Steps
1. Receiving a request
   - When an employee reaches out, respond to let them know to do the Onboarding steps seen in the User Onboarding section. 
2. Acknowledge the ticket
    - When acknowledging the ticket, add a ticket emoji to the message, and add an :ack: emoji to the message to assign it. 
3. Validate the user has requested specific repositories 
    - Reply to the user to ask for specific list of the repositories that they need access to, and their manager or team lead should be able to give them the repository names. 
    - Most times, the user will ask for access to the "ULP", <font color="red"> and users WILL NOT get access to all the repositories.</font>
4. Obtain required approvals
    - Look up the requester's manager in the orgization chart on the SharePoint site
    - Add two comments on the Jira ticket:
      - comment to an admin to let him know the new github user
      - comment to the user's manager to obtain approval of the request

5. Add user information to tracking page

6. Add user to AWS SSO via Terraform - Source Code Changes and Applying the changes
- Source Code Changes:
    - Update Terraform HCL in GitHub repository
    - add new user at the bottom of users.auto.tfvars
    - Assign the user to GitHub Group

- Applying the Changes
    - Commit changes using the following message format:
        - \<jira ticket> - \<message>
    - Create Branch
        - use the Jira ticket id
    - Create Pull Request
        - limit changes to one change from above, and use the same commit message as the title fo the PR
    - Terraform Plan will automatically run the preview the changes
        - changes should be reviewed at Terraform Cloud
    - Repository admin will need to approve and merge the Pull Request
    - When the PR is merged, the changes will be Auto-Applied
    - Log in to ULP-Root AWS Console and review the user information in IAM Identity Center
    - Reply on the Jira ticket (*or Slack Thread where the Jira ticket was created*)

7. Go to the GitHub SBA-ULP People and find the newly joined user 
   - Tips:
       - With AWS SSO, GitHub does not have an easy way to look up user by email address
       - Ask the user for their GitHub username
       - Most people use some form of thier real name 
       - Look through all users and find one that is not assigned to any teams.

    - IF you cannot find a user, you will need to reply on the Jira ticket to remind them to go through the AWS SSO setup process. 

8. Add the user to the relevant team based on thier desired repository access request
    - The prefix of the Team names match the prefix of the repository's name.
    - (Optional) if user is added one of the LOS or SBA-ULP Django repo, Add the user to one of the Lenders-Cooperative read only teams
      - The LOS and SBA-ULP Django applications have pip and npm dependencies on projects in the Lenders-Cooperative organization that require authorization to download.
      - <font color="red"> ask Michael.</font>

9. User will receive an email from GitHub automatically to let them know that they have been added to the team
10. Mark the CID Jira ticket as **DONE**



## User Onboarding

1. Requesting Access

    - Go to [(https://myaccess.microsoft.com/)](https://myaccess.microsoft.com/), and log in with your STG account. Look for the access package that you want to request access to and click request. This will send an email to your manager that they will approve granting you access.
2. Enable 2FA on your Personal GitHub
3. Go to  [(https://myaccess.microsoft.com/)](https://myaccess.microsoft.com/) -  look for the GitHub App, sign in using your STG Microsoft AD SSO to link your AD to GitHub
3. Add your STG email to your GH profile
