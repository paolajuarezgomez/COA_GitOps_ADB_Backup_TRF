# COA Deploy TRF with GitHub UseCase. 
# -- How to build a pipeline with GitHub Action  --

## ✅ Showcase

GitHub Actions is a continuous integration and continuous delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline. You can create workflows that build and test every pull request to your repository, or deploy merged pull requests to production.

During this UseCase we're going to:

* Use Github Actions to build different pipelines.
* Create a test pipeline.
* Deploy IaC using Terraform

## ✅ Usage

The first thing you’ll need to do before your GitHub Actions can run is to add your credentials to the repository. To do this you will need to follow these steps:

* Navigate to your repository and select the Settings tab.
* Once there you should see on the left a Secrets section third from the bottom of the list, click on that.
* Click on the New repository secret button.
* Add the next secrets:

````
user_id
api_fingerprint
token
````
* *token* is a personal [github token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token).

* Clone this repo in GitHub and create you own repository.
* The pipelines configuration is defined in .github/workflows, in this case we have created plan.yaml, unit.yaml and apply.yaml
* Add your *api_private_key* to the file **user.pem**
* Rename the file **terraform.tfvars.template** to **terraform.tfvars** and add the values of your *tenancy_ocid* and *compartment_ocid*
* Define the values desired in the  **coa.auto.tfvars**

* Change you repo code, for example change the ADB name, and do a "merge pull request" to deploy the changes. It will deploy this enviroment:
![mergepullrequest](images/pipeline1.png)
![mergepullrequest](images/pipeline1.png)

* This is the outcome of actions/github-script@v6 , you can review the plan outcome before do the merge.
![output](images/OutcomePlan.png)

* When you do the merge the workflow with the apply job is launched.
![meergeends](images/meergeends.png)

* If we review the pipelines ( plan and apply) in the tab "actions" 
![tabactions](images/tabactions.png)

* We can see the different workflows/pipelines steps...

![workflow](images/workflow.png)

![plan](images/Plan.png)
![plan1](images/Plan1.png)
![apply](images/Apply.png)
![apply1](images/Apply1.png)

![Provisioning](images/Provisioning.png)

* Check that now you can see the database provisioned in your compartment.
![console](images/console.png)

* After the provisioning, the outcome of the apply step is showed in the merge request page.
![console](images/OutcomeApply.png)

* Remove manually (using OCI Console) the ADB created previously.

If you need help, ask us in the slack channel #iac-enablement

## ✅ References
* [https://acloudguru.com/blog/engineering/how-to-use-github-actions-to-automate-terraform](https://acloudguru.com/blog/engineering/how-to-use-github-actions-to-automate-terraform)
