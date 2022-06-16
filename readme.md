
# Onboarding

**This onboarding material is focused on the general requirements for members of the HSCP ColeSlaw development teams.  Members of the SRE team who support the HSCP ColeSlaw offerings will need the access described here, as well as additional access described in the SRE onboarding. (TODO: Find SRE onboarding materials to link here)**

The HSCP ColeSlaw platform offerings (Watson Query and DB2 on Cloud) require access to some specific development tools and resources. They are listed below, along with the means of how to request access.  Following the [here](#obtaining-privileges) on how to request access, the [Education Sessions](#-education-sessions) section contains links to HSCP ColeSlaw education presentation recordings.  Additionally, there is a [Development Loop Example](#development-loop-example) section that contains a sample walk through of a simple development change.

If you have any questions or issue with the instructions below, please contact your manager or chrisr@ca.ibm.com for assistance.

## Obtaining Privileges

To perform any tasks some level of privileges is needed. Several of these access requests may require additional steps or/and may take some processing time.

### Github

The bulk of the HDM Services Common Platform (HSCP) components are found in the BlueTardigrade github.ibm.com organization, so access to that org is required.  Additionally, the dv-images repo, as well as the Watson Query specific github tracker are found in the data-virtualization (old name for Watson Query) organization, so you may also need access to that repo if you are going to be doing any work with the Watson Query service.

See the [Github Access requests](githubrequests.md) page for details about how to request access.  Typically, you will only need `Write` access to these orgs. 

### IBM Cloud Account 

The HSCP based services use a common layout of having 2 IBM Cloud Accounts per service.  One account is used to host dev/test infrastructure, and the other hosts production (and sometimes pre-prod/staging) infrastructure. Typically, you will need access to the dev/test account for one or more services so that you can test code changes, and push new containers to the dev container registry.

#### **Watson Query**

*If you will be doing development or support/ops work for the Watson Query service, you will need to request access to the Watson Query IBM Cloud accounts.*

The Watson Query dev and prod account are administered by the WAMS team.  See their [access request readme](https://github.ibm.com/aps-container-service/wdp-ams-devops/blob/master/documentation/Account/DVaaS-On-boarding-Instructions.md) for details. 

- most developers can just submit requests based on the [DVDEV Account access requests](https://github.ibm.com/aps-container-service/wdp-ams-devops/blob/master/documentation/Account/DVaaS-On-boarding-Instructions.md#dvdev-account-access-requests) section, to get the dev account access
- for members of the OPS/SRE team, and for senior developers who are SMEs, submit a request using the [DVPROD Account access requests / dvprod access for dv and dash customer support teams](https://github.ibm.com/aps-container-service/wdp-ams-devops/blob/master/documentation/Account/DVaaS-On-boarding-Instructions.md#dvprod-account-access-requests) section, to get the prod account access.

#### **DB2 on Cloud**

*All developers and SRE members, for both DB2 on Cloud and Watson Query will need to request access to the DB2 on Cloud dev account at least, because it contains the development container registry that is used for all of our offerings*

The DB2 on Cloud dev and prod accounts are managed by the DB2oC development and ops team directly.  To request access:

1. Bring up the [AccessHub manage my applications](https://ibm.idaccesshub.com/ECMv6/request/manageRequest) page.  (use your W3 credentials to login)  If for some reason, you can't access AccessHub, contact your manager for assistance.
2. If you see `SOS IDMgt` in the list of existing Instances you have access to, continue to step 3. below.  If not, go to step 4 below.
3. You already have access to the `SOS IDMgt` Instance.  To get access to the DB2oC IBM Cloud accounts, you need to request additional access within that account.
    1. Hover over the `SOS IDMgt` entry in the list, and click the Modify button that will become available.
    2. In section 2, Select Brand, select `BU166-DB2OC` from the dropdown.
    3. Click the `I confirm there are no SOD conflicts with this request` checkbox.
    4. In the Groups section click the Add button.  
    5. In the popup Groups modal, select the one or more groups that match your role:
        - `BU166-DB2OC-DB2-DEV` : for developers to allow access to the DB2 on Cloud dev and test IBM Cloud account and the associated clusters (**all developers need this**)
        - `BU166-DB2OC-DB2-SME` : for developers who are considered SMEs (Subject Matter Experts) and who will need access to the DB2 on Cloud production IBM Cloud account and the associated clusters to support the SRE team while investigating customer issues
          - This is not typically needed for new hires in on the development team 
          - Discuss with your manager if you aren't sure if you need this
        - `BU166-DB2OC-DB2-PROD-USER-OPS` : for members of the SRE/OPS teams who require access to the production DB2 on Cloud IBM Cloud account and the associated clusters to support customer productions deployments
        - `BU166-DB2OC-DB2-PROD-USER-OPS_EU` : for members of the SRE/OPS teams who require access to the special production EU Cloud IBM Cloud account and the associated clusters to support EU customer production deployments
          - Only members of the team who reside in an EU country may request this
          - Discuss with your manager if you aren't sure if you need this
        - `BU166-DB2OC-DB2-SME_EU` : for developers who are considered SMEs (Subject Matter Experts) and who will need access to the special EU DB2 on Cloud production IBM Cloud account and the associated clusters
          - Only members of the team who reside in an EU country may request this
          - This is not typically needed for new hires in on the development team
          - Discuss with your manager if you aren't sure if you need this
        
      After selecting the group(s) your role requires, click the Done button at the bottom of the Modal.
    6. Click the Review button.
    7. On the Review page, enter some text in the `Business Justification` section at the bottom.  
    8. Click the `***By clicking the "Submit" button on this page, I confirm that I have reviewed the access which is requested and this access is needed to perform required functions in the assigned job.` checkbox, and click the Submit button.
    9. Your access request will go through a few approvers. To view your request status, use the [Request History](https://ibm.idaccesshub.com/ECMv6/request/requestHistory)  AccessHub function.  Once all approvals are complete, you should have access to request IBM Cloud Account(s).
4. You do not yet have access to the `SOS IDMgt` application Instance.  You will need to request access to it, and request the specific access within the application for the DB2oC account(s).
    1. Click the [Request New Access](https://ibm.idaccesshub.com/ECMv6/request/applicationRequest) tile.
    2. Search for `SOS IDMgt`.
    2. Hoever over it in the list, and click the Request New Account option for it.
    3. In the Account Name field, enter a short username that you want to use as your SOS id.  
    
        **In addition to providing a way to request access to the DB2oC IBM Cloud accounts, we also make use of a lot of other tools that the SOS team provides, so you will need to use this id and its associated password to login to some of those tools.**
      
    4. Make sure the Account Type drop down is set to `User`.  
    2. In section 2, Select Brand, select `BU166-DB2OC` from the dropdown.
    3. Click the `I confirm there are no SOD conflicts with this request` checkbox.
    4. In the Groups section click the Add button.  
    5. In the popup Groups modal, select the one or more groups that match your role:
        - `BU166-DB2OC-DB2-DEV` : for developers to allow access to the DB2 on Cloud dev and test IBM Cloud account and the associated clusters (**all developers need this**)
        - `BU166-DB2OC-DB2-SME` : for developers who are considered SMEs (Subject Matter Experts) and who will need access to the DB2 on Cloud production IBM Cloud account and the associated clusters to support the SRE team while investigating customer issues
          - This is not typically needed for new hires in on the development team 
          - Discuss with your manager if you aren't sure if you need this
        - `BU166-DB2OC-DB2-PROD-USER-OPS` : for members of the SRE/OPS teams who require access to the production DB2 on Cloud IBM Cloud account and the associated clusters to support customer productions deployments
        - `BU166-DB2OC-DB2-PROD-USER-OPS_EU` : for members of the SRE/OPS teams who require access to the special production EU Cloud IBM Cloud account and the associated clusters to support EU customer production deployments
          - Only members of the team who reside in an EU country may request this
          - Discuss with your manager if you aren't sure if you need this
        - `BU166-DB2OC-DB2-SME_EU` : for developers who are considered SMEs (Subject Matter Experts) and who will need access to the special EU DB2 on Cloud production IBM Cloud account and the associated clusters
          - Only members of the team who reside in an EU country may request this
          - This is not typically needed for new hires in on the development team
          - Discuss with your manager if you aren't sure if you need this
        
      After selecting the group(s) your role requires, click the Done button at the bottom of the Modal.
    6. Click the Review button.
    7. On the Review page, enter some text in the `Business Justification` section at the bottom.  
    8. Click the `***By clicking the "Submit" button on this page, I confirm that I have reviewed the access which is requested and this access is needed to perform required functions in the assigned job.` checkbox, and click the Submit button.
    9. Your access request will go through a few approvers. To view your request status, use the [Request History](https://ibm.idaccesshub.com/ECMv6/request/requestHistory)  AccessHub function.  Once all approvals are complete, you should have access to the requested IBM Cloud Account(s).
    
##### **DB2 on Cloud EU Emergency Access**

Occasionally, non-EU resident members of the SRE or Development team will require temporary access to the EU clusters to provide support for critical Sev 1 issues.  IBM Cloud provides this [process guidance](https://pages.github.ibm.com/ibmcloud/Security/guidance/AccessHub-EUCloud.html) in that situation.

To request this temporary access, follow the instruction above for requesting additional access to the `SOS IDMgt` AccessHub application, but under the `BU166-DB2OC` brand, select the group `BU166-DB2OC-DB2-PROD-USER-OPS_EU_emerg`.  

Once the Sev 1 issues has been resolved, this temporary access will be removed.

### **Jenkins**

We have a few TaaS (Toolchain-as-a-Service) based Jenkins servers that are used to automate much of our pipeline work.  

- https://hyc-dvaas-team-jenkins.swg-devops.com/ : all members should have at least read access to this Jenkins server, so that you can view job output, and executed jobs.  You may also need Write access if you want to modify or create jobs.  This server is used to drive the CI and CD pipelines for all of the HSCP ColeSlaw offerings.  (DB2oC and Watson Query)
- https://hyc-db2oncloud-jenkins.swg-devops.com/ : if you are a DB2 on Cloud developer, you will want to request at least read access to this Jenkins server.  It is used to run specific testing for the DB2 on Cloud offering. 

Access is currently granted manually, so ping chrisr@ca.ibm.com (@chrisr) in slack) for access requests.  This will eventually be moved into AccessHub.  The Artifactory access below is granted the same way, so just ping Chris once with all of your access requests.

### **Artifactory**

The TaaS Artifactory server is used to host build artifacts needed for our services, both in the form of libraries and in some cases docker containers.  

#### HSCP ColeSlaw Artifactory Repositories 

We have a number of Artifactory repositories that are used as part of doing development of our offerings.  The most important two, and what you need to request access to are:

- dashtx-generic-local
- hyc-bluetardigrade-team-db2oc-db2oncloud-docker-local

Access is currently granted manually, so ping chrisr@ca.ibm.com (@chrisr) in slack) for access requests.  This will eventually be moved into AccessHub as well.

#### IBM-Cloud-Databases team Artifactory Repositories

If you will be doing any work with the `Front-End` components of the platform, and specifically you will need the ability to develop and test changes to the `middle-end` component, you will also need to request access to the `IBM Cloud Databases` team's artifactory repository, specifically, their ruby-gems repo.  Please confirm with your manager, or one of the senior developers to make sure that you need this authority, because it is kind of a hassle to get, and should only be done if absolutely needed.

This access is requested via AccessHub.

1. Use the [AccessHub Request New Access](https://ibm.idaccesshub.com/ECMv6/request/applicationRequest) section.
2. Search for `IBM Cloud Databases`, hover over the line, and select the `Request New Account` option.
3. You will need to follow the instruction in the "Onboarding Employees" link before you will be approved.
4. In the Team section, click the Add button, and select the ibm-collaborator Team.
5. Click the Review button.
6. Provide Business Justification, something along the lines of, `I need access to the ruby gems artifactory repository to perform downstream development of the middle-end ICD component for Hybrid Data Management`
7. Click submit.
8. There are a few approvals to go through, and final approval will not be given until you have completed all of the onboarding requirements, which may include HIPAA certification.   
9. To check on the status of your approval, or to contact the approvers, use the [Request History](https://ibm.idaccesshub.com/ECMv6/request/requestHistory)  AccessHub function. 

### **ServiceNow (?)**

TBD, not needed right now.

### **Vault**

Part of getting [icdflow](../../architecture/tools/icdflow/README.md) setup. See the instructions there for details.

### **SOS PIM (Privileged Identity Management)**

Lookup the [SOS Privileged Identify Management](https://pages.github.ibm.com/BlueTardigrade/db2oc-docs/common/architecture/tools/SOSPIM/) page to identify privileges relevant to your work.

If you need to be able to update the Staging or Production IBM Cloud Global Catalogs, you will need 

* ***SOS IDMgt -> BU166-DB2OC-Dev-Creds-WQ*** (Watson Query Staging)
* ***SOS IDMgt -> BU166-DB2OC-Prod-Creds-WQ*** (Watson Query Production)
* ***SOS IDMgt -> BU166-DB2OC-Dev-Creds-DB2OC*** (DB2OC Staging)
* ***SOS IDMgt -> BU166-DB2OC-Prod-Creds-DB2OC*** (DB2OC Production)

For details about how to request these, see the linked page above.  

### Slack

Slack is the corporate messaging and collaboration application used throughout IBM.  For more information, see the [Slack User Guide](https://w3.ibm.com/#/support/article/slack_users_guide/overview)

By default, all IBM employees should have access to the IBM Enterprise Slack uber workspace.  Within that overriding IBM Workspace, there are many (>7500) more granular workspaces.  For the HSCP ColeSlaw products, the channels we use should all be available in the `IBM Data and AI` workspace. 

Steps:
1. While you can use slack in the browser, it is a much better experience to install the application.  It is typically pre-installed on most IBM Mac and Lenovo laptops, but if not, see the [Getting Started](https://w3.ibm.com/#/support/article/slack_users_guide/install) docs for information on how to install.
2. Make sure to join the `IBM Data and AI` workspace listed above.  Go to the [Workspaces at IBM](https://w3.ibm.com/#/support/article/slack_users_guide/install) page, search for the workspace, click the View Details button, and select Request to Join.
3. Once you have access to the workspace, see the table below for the channels that you should/can subscribe to.  Note that some of the channels are private.  If you need access, please DM @chrisr in slack.

#### Most Important

| Channel                                        | Details |
| ----------                                     | ------  |
| cloud-dev-hdm                                  | Primary channel for announcements and celebrations for all of the HDM offerings within HDM, not just the HSPC ColeSlaw ones |
| db2oc-nebula                                   | Primary channel for DB2onCloud development team discussions |
| dvaas-dev                                      | Primary channel for Watson Query development team discussions |
| hdm-pipeline-notifications                     | All production builds and cluster updates are reflected in this channel |
| dashdb-learning                                | Used for DB2oC development/ops discussions |
| dv-cloud-learning                              | Used for Watson Query development/ops discussions |
| console-db2oc                                  | Used to discuss production issues with the DB2 on Cloud console development team |
| dv-cloud-infra                                 | Used to discuss Watson Query infrastructure requirements with the WAMS team, who manages the dv IBM Cloud accounts |
| dv-console-dev                                 | General discussion with the Watson Query console development team |
| dvaas-qa                                       | **Private, need invite** General discussions with the Watson Query QA team |
| dashdb-tx-reviews                              | **Private, need invite** PR review requests for the DB2oC development team |


#### Informative

These channels may or may not be of interest

| Channel                                        | Details |
| ----------                                     | ------  |
| cdcp-adopters                                  | Primary channel to ask question of the IBM Cloud Databases team |
| db2oc-console-dev                              | **Private, need invite** General discussion with the DB2oC console development team |
| db2oc-v2-updates                               | Discussion with the DB2oC Ops team related to customer formation updates | 
| hdm-cloud-monitoring                           | Contains automated messages showing overall Operations health for all of the HDM Services 

## **Tools**

It is highly suggested to use a virtual environment for installation of Python modules. That will save you a lot of time in case you need to reinstall some of the components/dependencies. The list below is just a baseline as it is not comprehensive and every repo development will come with its own characteristics. 

* **Python version 3.8** or higher
* [Docker](https://www.docker.com/) (additional steps needed to receive the [license](https://w3.ibm.com/w3publisher/docker-desktop)) or possibly a different compatible containerization solution like [podman](https://podman.io/getting-started/installation). Note that docker has been the prevalent choice for the development process and the alternatives may cause some issues.
* [ibmcloud](https://cloud.ibm.com/docs/cli) - The CLI for IBM Cloud 
* [icdctl](https://github.ibm.com/BlueTardigrade/icdctl) - ibmcloud abstraction that will allow you to connect to clusters and investigate them.
* [icdflow](https://github.ibm.com/BlueTardigrade/icdflow) - The tool will allow you to build a developed repository and deploy it into a cluster specified by icdctl.
* All the dependencies for the aforementioned tools

## Education Sessions

A number of education talks have been delivered by HSCP ColeSlaw SMEs that are a *must* for new team members.  The playback recordings for already completed talks, as well links to sign up for any additional upcoming talks, are located [here](https://ec.yourlearning.ibm.com/w3/series/10245435?layout=grid).  Please contact chrisr@ca.ibm.com if you have any issues accessing them.

## Development Loop Example

The ColeSlaw platform is made up of micro-services and configurations that are deployed as Kubernetes artifacts and are built from code stored in GitHub repositories.  As part of the development process, the containers that are used to implement the Kubernetes artifacts may be built locally from local repository changes using the [icdflow](https://github.ibm.com/BlueTardigrade/icdflow) tool. The created image can be then be uploaded to a development kubernetes cluster for testing, before submitting the changes to the Continuous Integration pipeline and using a PR to merge the changes into the production branch.

The following example uses the `ibm-cloud-frontend` repository and should demonstrate the approximate development workflow for most scenarios. Changes introduced into the codebase and pushed into the cluster should be communicated with other team members beforehand, as only one person can change a specific component residing on a specific cluster. Otherwise, any modifications tested by someone else will be overwritten in a process of component substitution.

1. Make sure that you have icdctl and icdflow installed properly on your laptop.

1. Make sure there is the [BlueTardigrade/ibm-cloud-databases](https://github.ibm.com/BlueTardigrade/ibm-cloud-databases) repo cloned on your environment and referenced as baseline in your icdflow configuration. See [step 6](https://github.ibm.com/BlueTardigrade/icdflow#step--6%EF%B8%8F%E2%83%A3) of icdflow README. **Because this repo is used by `icdflow install`, it is critical that you keep the hdm_main branch of this repo up to date, because it changes a lot.**.

2. Also clone down the [BlueTardigrade/ibm-cloud-frontend](https://github.ibm.com/BlueTardigrade/ibm-cloud-frontend) repository.  Most of the component repositories don't have any direct dependencies on other components, but IBM Cloud Frontend is different, and does require that the [BlueTardigrade/frontend-engine](https://github.ibm.com/BlueTardigrade/frontend-engine) is also downloaded.  Those two cloned repos should reside at the same directory level.

2. Introduce a codebase change:

    Checkout a new development branch for the development repository, and make a code change.  In order for the CI pipeline to properly buid your branch, the dev branch name __MUST__ follow the convention:
    
    `hdm_<your short name>_t<tracker>` or 
    `hdm_<your short name>_<change desc>`
    
    e.g. `hdm_chrisr_t12345` or `hdm_chrisr_my-operator-change`.   
    
    **Ideally, the same branch should also be checked out in the ibm-cloud-databases local repo also.  When you run `icdflow build` for your code changes, a new container will be built, and the icdflow will update the helm charts in the ibm-cloud-databases repo on whatever branch is checked out, so its important that you are using the same dev branch.** 
       
      ![image](images/code_change.png)

3. Log into the IBM Cloud and the DB2onCloud_dev development container registry 

    When running `icdflow build`, the newly built container (if successfully built) will be pushed into the db2oncloud_dev container registry, so you need to have first successfully logged into the container registry before that will work.

    1. Log in to the IBM Cloud DB2oC dev account
     
     ![image](images/cloud_login.png)
     
    2. It is important to connect to the correct account and region, the one containing the required container registry:

      ![image](images/cloud_login_2.png)

    3. Login to the container registry:

      ![image](images/cr_login.png)

4. Once logged into the container registry, the `"icdflow build"` command can be invoked. The command is going to build the complete image for the `ibm-cloud-frontend` component and push it into the container registry:

    ![image](images/icdflow_build.png)

    Possible issues might occur when having insufficient privileges for artifact pulling. If so, please refer to the `Artifactory` subsection in the **`Obtaining Privileges`** section.

5. The sha digest for the newly built container image will also be updated in the local `ibm-cloud-databases` repository yaml file responsible for the `ibm-cloud-frontend` component:

    ![image](images/sha_change.png)

6. Once built successfully and added to the local ibm-cloud-databases helm charts, the image can be uploaded into a development cluster for testing.  There are several methods for doing this.  One is to manually update the kubernetes deployment artifact with the SHA digest of your newly built development container.  Another is to use `icdflow install`.  The latter is used in the sample below.  For a review of both of these, as well as other methods of deploying your dev changes to development clusters, watch the [HSCP Education Series: Pipeline, Release Management and Automated QA (Part 2)](https://ec.yourlearning.ibm.com/w3/series/10245435?layout=grid) recorded playback. 

    1. Target a development cluster of choice. A list of clusters can be obtained using the `"icdctl cluster"` command. Be wary that all of the clusters are divided into two types: `control-plane` and `data-plane`. The exact component belonging is stated in the FAQ section. Since the `ibm-cloud-frontend` is a part of the `control-plane`, such cluster will be targeted: 
   
      ![image](images/icdctl_cluser_targeted.png)
    
     When doing deployment of development code for testing keep 2 things in mind:
     
        1. Only to deploy to development clusters that are associated with the development team you are on:
          - Watson Query: 
            - dv-icd-dev-us-south-db-zsnke
            - dv-icd-dev-us-south-cp-witdf
          - Db2oC:
            - db2-icd-dev-us-south-db-awlkd
            - db2-icd-dev-us-south-cp-mbepd
            - db2-icd-dev-us-south-db-k6pub
            - db2-icd-dev-eu-gb-cp-fe5
            - db2-icd-dev-eu-gb-db-397
        2. Because the dev clusters are shared, its important to check and see if other developers will be impacted by your changes, so check/post to the appropriate slack channel for Watson Query (dvaas-dev) dev or DB2oC dev (db2oc-nebula).

    2. All pods in the cluster can be printed out. The pod namespace is specified with the `-n`  flag. The control plane components belong to the `icd-control` namespace:

        ![image](images/pods_namespace.png)

    3. Three replicas of the `ibm-cloud-frontend` are present on the cluster, as seen in the previous screenshot. The pod can be also described for more information:

        ![image](images/describle_frontend.png)
  
    4. Use the `icdflow install` command. The command uses the sha value change in `ibm-cloud-databases` and substitutes the existing `ibm-cloud-frontend` pods with the changed ones:

        ![image](images/icdflow_install.png)

    5. Proceed with testing of your changes in the cluster.
    
    6. A simple way to check the logs for the updated components is to use [logDNA](https://cloud.ibm.com/observe/logging) and choose the correct logDNA instance:
    
      ![image](images/log_aggregator_choice.png)

    7. One way to observe the code change introduced previously, is to create a new WQ Enterprise dev instance or Db2onCloud dev instance. It can be done through the [IBM Cloud test page](https://test.cloud.ibm.com/). 

      ![image](images/enterprise_plan.png)

    8. After creating a new instance, the following should be seen in the LogDNA output based on the code change made above:
        
      ![image](images/log_output.png)   

10. After your testing is complete, push your dev branch changes to GitHub to have the CI pipeline build it, in preparation for creating your PR to merge your changes into the hdm_main production branch.  For more details on what the pipeline will do, see the [Stages documentation](https://pages.github.ibm.com/BlueTardigrade/db2oc-docs/common/architecture/pipeline/Stages.html).  

11. It's important to always reverse development component changes that have been applied to the clusters back to the hdm_main version as soon as the testing is over. An easy way to achieve this is to checkout hdm_main in your local `ibm-cloud-databases` repository, pull down the latest code from GitHub, and re-install the modified component using `icdflow install`. This assumes that your dev changes were made to a dev branch in the local ibm-cloud-databases repo.  If they weren't, and the changes were made to the local hdm_main branch, then those changes will need to be reverted before re-deploying.  Another way to revert the development cluster back to the hdm_main level is to use the [ICD-Install-Cluster](https://hyc-dvaas-team-jenkins.swg-devops.com/job/ICD-Install-Cluster/build?delay=0sec) job in Jenkins.
