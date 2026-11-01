ASSIGNMENT 1
1. In git there is a repository not storing the file directly in the repository. inside the repo, there is a                    particular layer  called MAIN branch .That is where storing all of them .

  when we create a branch we have 2 way to create

       a. create on the remote repo.(to be used by everyone in the project)

       b. directly created on local repo.(if we creating a branch only for our work )

 BRANCHING STRATEGY : It is a set of rules used by software development team to manage code changed in a version controlling s/m like Git.

To choose which branch we wants to work ,we can use the command called "$git checkout branch name" .

FEATURE BRANCHING : It is the development branch in which developers will actually write, modify, push the code. feature means functionality release ,whatever the functionality to release.

created a new feature branch develop the code , once the code is developed we will merge to integration branch. create a integration branch from main branch . from that if for the product or the microservice , if we deploying new feature or modifying or doing some bugfix for every changes that we where doing as a feature . in micro service each feature having separate branches .in branches integration branch contains all the combined branches.

from the integration branch we create a new release branch .then release the code or put in to the production . then merge code into main branch to keep it as a stable copy. 

once the release is done , to fix the bugs that to be given by the particular customer we create a branch called BUGFIX .

TRUNK-BASED DEVELOPMENT : it's another branching strategy to makes true continuous integration possible .every change merged to the main branch triggers the ci pipeline automatically . unit test , integration test and other checks run on every commit .because developers commit often and each code change is small, problem are easier to isolate and fix .

    -> unit test : developer does . test after the developer  modified the code . entire code then generate a                             product  .

    -> functional test : validate the code . QA team will do it .

    -> integration test : testing to check whether all the individual feature are working together .

    -> regression test : check whether existing  functionality and feature is working with new feature.

frequently commits simplify debugging and rollback .

 8 core stages of the DevOps Lifecycle from the moment code is planned until it is running.

   1) Plan : create roadmaps , Backlog management, sprint planning, and writing user stories.

               Common Tools: Jira, Azure , Boards 

  2) Develop : Write high-quality, version-controlled source code for features or fixes. Writing code,                                    performing code reviews, and managing branch merges.

                      Common Tools: Git, GitHub, GitLab

  3) Build : Compile source code and package it into executable artifacts or libraries. Merging code into                         shared repositories and triggering automated compilation.

                 Common Tools: Jenkins, Maven

  4) Test : Validate software quality, find bugs early, and ensure stability before release. Running                                   automated . unit, integration, and regression tests.

  5) Release : Package and approve the validated build for deployment into staging or production .Version                           tagging, release scheduling, and artifact management.

                           Common Tools: Jenkins, Bamboo, GitLab CI/CD

  6) Deploy : Push the application safely into the live production environment with minimal downtime.                                 Infrastructure-as-Code provisioning and automated rollouts.

                     Common Tools: Kubernetes, Docker, AWS, Azure, Terraform.

  7) Operate : Manage the running application in production and maintain system reliability. Server                                      configuration, container orchestration, and routine maintenance.

                      Common Tools: Docker, Kubernetes

  8) Monitor : Track live application performance, user activity, and system health . Collecting logs,                                       tracking error rates, and feeding real-world data and user feedback back into the Plan stage                         to restart the loop.

                       Common Tools: Prometheus, Grafana .

ML Ops life cycle stages

contains 7 phases

     1. DATA COLLECTION : which means previous or historic production data .

     2. ML DEVELOPMENT : the end-to-end process of building, training, testing, and deploying computer              programs that learn patterns from data to make predictions or decisions without explicit rule-based              programming .

     3. BUILG ML MODEL : To build a machine learning (ML) model means to create a computer program                 that can automatically recognize patterns, find hidden insights, and make decisions from data                       without being explicitly programmed for that specific task .

     4. TRAIN THE MODEL :  it is teaching the machine to learn from our data [data +algorithm=model].

     5. EVALUATE / TESTING MODEL :  means measuring how well a trained model generalizes to unseen                data, checking its behavioral stability, and verifying that the surrounding data and infrastructure                  pipelines work reliably before and after deployment

     6. DEPLOY THE MODEL : (inference) making model live and  usable for real people, not just a project .

          in ML Ops deploy means where we put the model (on a server) , inference means what the model                  does there .

      7. MONITOR THE MODEL : keeping an eye on our model after it is deployed ,means to check if it is still            working correctly . in another words  monitor the model means , health checkup of our live model                to make sure it is still accurate , fast and useful .         

4. different testing process in ML Ops :  Include 4 diff type of testing 

     pipeline validation : Dry run on the model to check whether its running , can it take i/p and give a              o/p . do we have the ability to train the model . this will be done on a dev environment .

     model validation :  split the data set into 80% and 20%. train the model with 80% dataset and use           the 20% database to evaluate . this will be done in QA environment . 

          .  it is connecting to dependency (DB, Kafka) .

          .  it is able to pull or push data 

     Inference testing : End to End application testing to check id model is working in the product                    Ecosystem. we can do load / performance test .

     shadow testing : By passing live production data , check whether our model is predicting properly.

 

        CODE PROMOTION HAPPENDS IN 3 STAGES

DEV ENVIRONMENT :- write new code , train a small model , test it  

STAGING / TEST ENVIRONMENT  :-when  dev code is working . we push it to staging branch  

PRODUCTION ENVIRONMENT:- (real users)  if staging passes all tests , code is promoted to main /prod branch .it gets deployed to real server where users use it .
