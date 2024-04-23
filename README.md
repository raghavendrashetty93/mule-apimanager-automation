# mule-apimanager-automation
# This is a workflow which Integrates GitHub with Mulesoft API Manager and Automatically Updates corresponding API's Asset Version in API Manager After Successful Code push.
GitHub Actions workflow to seamlessly update API version in Mulesoft API Manager
In this step-by-step tutorial, learn how to create an automation using GitHub Actions which updates Mulesoft API’s Asset Version in API Manager.



Overview: This workflow automatically updates corresponding API's Asset Version in Mulesoft API Manager after every successful code commit done through GitHub. 

It extracts RAML Asset Version from RAML Dependency in POM file and seamlessly updates Asset Version shown in below image, eliminating the need to manually update version after every new API version’s release into Exchange.



## Prerequisites
Maintaining RAML as dependency in pom.xml file. Here ‘groupId’ is Anypoint Organization ID of your Organization and version signifies the RAML version.

    <dependency>
      <groupId>d422df1e-cdf7-41a5-a47d-8710f8b89704</groupId>
      <artifactId>api-manager-automation</artifactId>
      <version>1.0.1</version>
      <classifier>raml</classifier>
      <type>zip</type>
    </dependency>

API Manager API and Auto Discovery Property in environment specific properties file.

## Workflow Creation

- Create GitHub Secret with name MULESOFT_ANYPOINT_PASSWORD and provide Anypoint Platform password as value. We can create GitHub secrets from the Settings page. It can be either Repository Secret or Organization Secret.
- Navigate to your GitHub repositories branch for which version update automation needs ro be configured.
- Click on ‘Actions’ and then click on ‘Configure’ button under ‘Simple workflow’
- You can optionally rename the name of the workflow.
- Update editor content under ‘Edit new file’ section, using below template.

### Update/Verify following in template:

S.No
Activity
Description
I
Update
Your Git Branch Names
II
Update
Your Clouhub Environment Id's of sandboxes.
III
Verify
Your properties file location in code
IV
Update
Syntax should be as per your properties file structure and also update autodiscovery property name.
V
Verify
Applicable only if your properties file follows .properties format.
VI
Update
Your Anypoint Platform credentials



- Commit changes into your desired branch. In this case its develop branch.
- Since it is a code commit, workflow will run and you can check the details in the console.
- Click on Details and you will be navigated to the console.
- Also you can login to Anypoint Platform to verify the update.

## Working

- The Workflow parses pom.xml file and extracts groupId, RAML version to be updated.
- Gets auto-discovery id from properties file.
- Gets environment id based on branch name.
- Get Access Token using your enterprise’s username and password.
- Invokes API Manager using Mulesoft Platform API’s.

Note: Please feel free to update the Workflow code accordingly as per your project's structure
