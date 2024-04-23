# mule-apimanager-automation
# This is a workflow which Integrates GitHub with Mulesoft API Manager and Automatically Updates corresponding API's Asset Version in API Manager After Successful Code push.

- GitHub Actions workflow to seamlessly update API version in Mulesoft API Manager.
- Updates Mulesoft API’s Asset Version in API Manager.
- Updates after every successful code commit. 

It extracts RAML Asset Version from RAML Dependency in POM file and seamlessly updates Asset Version, eliminating the need to manually update version after every new API version’s release into Exchange.

## Prerequisites
Maintaining RAML as dependency in pom.xml file. Here ‘groupId’ is Anypoint Organization ID of your Organization and version signifies the RAML version.

    <dependency>
      <groupId>137c2019-fcd5-41b8-8525-313ae789beef</groupId>
      <artifactId>mule-apimanager-automation</artifactId>
      <version>1.0.0</version>
      <classifier>raml</classifier>
      <type>zip</type>
    </dependency>

API Manager API should be created and Auto Discovery Property should be maintained in environment specific properties file.

## Workflow Creation

- Create GitHub Secrets with name MULESOFT_ANYPOINT_USERNAME, MULESOFT_ANYPOINT_PASSWORD and store Anypoint Platform credentials. We can create GitHub secrets from the Settings page. It can be either Repository Secret or Organization Secret.
- Navigate to your GitHub repositories branch for which version update automation needs ro be configured.
- Click on ‘Actions’ and then click on ‘Configure’ button under ‘Simple workflow’
- You can optionally rename the name of the workflow.
- Update editor content under ‘Edit new file’ section, using below template.

## Reference Workflow
https://github.com/raghavendrashetty93/mule-apimanager-automation/blob/main/.github/workflows/update-autodiscovery-id.yml

### Update/Verify following in above Reference Workflow

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

- Commit changes into your desired branch. In this case its main branch.
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
