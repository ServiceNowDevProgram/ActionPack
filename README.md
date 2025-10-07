<img width="1280" height="250" alt="actionpack banner" src="https://github.com/user-attachments/assets/08926d1f-7bda-433f-91af-23fb0a2cde0b" />

# ActionPack: An action-packed pack of Flow Actions!

Welcome to ServiceNow's ActionPack community repository, managed by the Developer Program and the sndevs Slack community.

> Interested in our other ServiceNow Hacktoberfest projects? See the main repository [here](https://github.com/ServiceNowDevProgram/Hacktoberfest) or see our official blog post [here](https://devlink.sn/hacktoberfest).

### Have you ever looked for an action in Workflow Studio, only to find that an appropriate utility or action is missing? 

ActionPack is designed to address this problem by crowdsourcing action definitions across the ServiceNow community that can be used by developers! It is built on the principle of "Many hands make light work", and is available for download and use in any ServiceNow instance.

> [!NOTE]
> In order to make all step types available, we recommend installing the ServiceNow IntegrationHub Enterprise Pack Installer plugin. The different installers are documented [here](https://www.servicenow.com/docs/bundle/zurich-integrate-applications/page/administer/integrationhub/reference/ih-plugins.html).
>
> The location these are installed depends on whether you are on a customer/vendor instance, or a PDI:
> - **Customer/Vendor**: Install the plugin from Now Support using the Automation Store: [ServiceNow IntegrationHub Enterprise Pack Installer](https://support.servicenow.com/now/en/pages/automation-store?id=ns_automation_store&plugin_sys_id=752e0d351b2d90101c8633f2cd4bcbc4) 
> - **PDI**: Install the plugin from the Developer site using the Manage Instance page: [Manage Instance](https://developer.servicenow.com/dev.do#!/manage-instance)

## Disclaimer

Please note the following:

1. **Community-Sourced Actions**: The actions found in this repository is contributed by members of the community and has not been vetted or officially endorsed by the repository owners.

2. **Use at Your Own Risk**: Users are advised to exercise caution and thoroughly review the actions when leveraging them in their ServiceNow instances. We strongly recommend a comprehensive review to ensure the actions align with your specific requirements and security standards.

3. **Reporting Mistakes and Issues**: If you come across any mistakes, issues, or improvements in the repository, we encourage you to report them as issues and consider contributing to the repository by submitting corrections or enhancements.

4. **No Warranty or Support**: This repository is provided as-is, without any warranties or guarantees. It does not come with official support from the ServiceNow team or the repository owners.

By installing the scope from this repository, you acknowledge that you have read and understood this disclaimer. Your use of the actions is at your own discretion and risk.

We appreciate your participation and contributions to this community-driven project. Let's collaborate to make it a valuable resource for ServiceNow developers and enthusiasts.

> [!IMPORTANT]
> 🔔🔔🔔<br>
> **_CONTRIBUTORS must follow all guidelines in [CONTRIBUTING.md](CONTRIBUTING.md)_** or run the risk of having your Pull Requests labeled non-compliant or as spam.<br>
> 🔔🔔🔔


## We invite you to contribute!

To contribute, just follow these steps:

1. Fork this repo (you get a point just by forking!)
2. Go to your ServiceNow instance
3. Go to a Source Control-enabled Studio:
    - On Zurich and above: `ServiceNow Studio`
    - On Yokohama and earlier: `App Engine Studio` or `Legacy Studio`
4. Using your fork of this application, import it from source control, using the `main` branch: 
    **Note:** If this is your first time using source control in this instance, create a credential as described by Earl [here](https://www.servicenow.com/community/developer-advocate-blog/source-control-in-servicenow-studio-complete-walkthrough/ba-p/3356303#create-a-credential-in-servicenow).
    - [SNS Import Instructions](http://servicenow.com/docs/bundle/zurich-application-development/page/build/servicenow-studio/task/sns-sc-import-app-source-control.html)
    - [AES Import Instructions](http://servicenow.com/docs/bundle/yokohama-application-development/page/build/app-engine-studio/task/source-control-import.html)
    - [Legacy Studio Import Instructions](https://www.servicenow.com/docs/bundle/yokohama-application-development/page/build/applications/task/t_ImportAppFromSourceControl.html)
5. Using a Source Control-enabled Studio, create a new branch and switch to it:
    - [SNS Create Branch Instructions](https://www.servicenow.com/docs/bundle/zurich-application-development/page/build/servicenow-studio/concept/sns-sc-create-versions-branches-git.html#title_sns-sc-create-repo-branch)
    - [AES Create Branch Instructions](https://www.servicenow.com/docs/bundle/yokohama-application-development/page/build/app-engine-studio/concept/create-versions-branches-git.html#title_source-control-create-branch)
    - [Legacy Studio Create Branch Instructions](https://www.servicenow.com/docs/bundle/yokohama-application-development/page/build/applications/task/t_CreateBranch.html)
6. Open your preferred studio experience
7. Create a new action, or update an existing action. See [CONTRIBUTING.md](CONTRIBUTING.md) for additional details.
8. Using a Source Control-enabled Studio, commit your changes to source control:
    - [SNS Commit Changes Instructions](https://www.servicenow.com/docs/bundle/zurich-application-development/page/build/servicenow-studio/task/sns-sc-commit-changes-to-repository.html)
    - [AES Commit Changes Instructions](https://www.servicenow.com/docs/bundle/yokohama-application-development/page/build/app-engine-studio/task/source-control-commit-changes.html)
    - [Legacy Studio Commit Changes Instructions](https://www.servicenow.com/docs/bundle/yokohama-application-development/page/build/applications/task/t_CommitChanges.html)
9. Submit a pull request to the ServiceNowDevProgram/ActionPack `main` branch

That's it! More detailed contribution instructions can be found [here](CONTRIBUTING.md)
