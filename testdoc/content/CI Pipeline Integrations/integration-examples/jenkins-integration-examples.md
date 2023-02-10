---
title: "Jenkins Integration Examples"
slug: "jenkins-integration-examples"
excerpt: "This section provides the Jenkins integration examples for different use cases."
hidden: false
metadata: 
  description: "Jenkins Integration Examples"
createdAt: "2021-09-16T09:40:43.848Z"
updatedAt: "2022-12-08T13:10:51.146Z"
---
## Example 1. Scan from the cloud using the Bright CLI (NPM installation)

To apply this option, you only need to install the Bright CLI globally on your Jenkins machine using the relative NPM command. 

### Prerequisites

- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) (`BRIGHT_TOKEN`) with the following scopes: `bot`,<br>`scans : run`,`scan : read`, and `scans : stop`.
- You have downloaded the Node.js plug-in to your Jenkins machine.
- You have created the `BRIGHT_TOKEN` environmental variable on your Jenkins machine.
- You have copied the Bright `PROJECT_ID` on the **Projects** page. If you do not specify the `PROJECT_ID` , the scan will be run under **Default** project. 

### Step-by-step guide

#### STEP 1 - Install the CLI

```bash
  sh 'npm install @neuralegion/nexploit-cli -g || true'
```



#### STEP 2 -  Run (retest) a scan

- If you need to run a new scan with a Crawler,  use the following script: 

```bash
  echo "Start Bright Scan 🏁"
           SCAN_ID=$(nexploit-cli scan:run --token ${BRIGHT_TOKEN} --name "Jenkins Scan" --crawler https://brokencrystals.com/ --smart)
           echo "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
```



- If you need to re-test a previous scan with its ID `OLD_SCAN_ID`, use the following script:

```bash
echo "Retest a scan"
         NEW_SCAN_ID=$(nexploit-cli scan:retest --token=$BRIGHT_TOKEN $OLD_SCAN_ID)
         echo "Scan was started with ID https://app.brightsec.com/scans/$NEW_SCAN_ID\n"
```



#### STEP 3 -  Poll the results

> 📘 Note
> 
> When polling the scan results, it is recommended to follow the fail-fast principle by using the `breakpoint` command.  See [Bright CLI Command List](/docs/command-list) for a full list of commands you can use in your Jenkins flow.

Poll the scan until it returns some issue, or its time runs out:

```bash
 echo "Wait for issues ⏳\n"
           RESULT=$(nexploit-cli scan:polling --interval 30s --timeout 20m --token $BRIGHT_TOKEN --breakpoint medium_issue $SCAN_ID)
           if [ -z "$RESULT" ]
           then
               echo "Failed to stop scan"
           else
               echo "Stop Scan 🛑"
               nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
```



#### STEP 4 -  View the  results

To view the scan results, go to the [Bright app](https://app.neuralegion.com). For the instructions, see [here](https://docs.neuralegion.com/docs/reviewing-scan-details#review-scan-results).

### Complete example

The following example is made up of the steps above and shows how to run a new scan using the Crawler discovery type:

```bash
pipeline {
 agent any
 environment {
   BRIGHT_TOKEN = "$BRIGHT_TOKEN"
   }
 tools {nodejs "node"}
 stages {
   stage("Install Dep"){
       steps{
           sh 'npm install @neuralegion/nexploit-cli -g || true'
       }
   }
   stage('Start Scan') {
     steps {
         sh '''#!/bin/bash
           echo "Start Bright Scan 🏁"
           SCAN_ID=$(nexploit-cli scan:run --token ${BRIGHT_TOKEN} --name "Jenkins Scan" --crawler https://brokencrystals.com/ --smart)
           echo "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
           sleep 10
           echo "Wait for issues ⏳\n"
           RESULT=$(nexploit-cli scan:polling --interval 30s --timeout 20m --token $BRIGHT_TOKEN --breakpoint medium_issue $SCAN_ID)
           if [ -z "$RESULT" ]
           then
               echo "Failed to stop scan"
           else
               echo "Stop Scan 🛑"
               nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
           fi
       '''
     }
   }
 }
}
```



## Example 2. Scan in the repeater mode using the Bright CLI (NPM installation)

To apply this option, you need to install the Bright CLI on your Jenkins machine and activate the Repeater using the Repeater ID and Bright API key. 

### Prerequisites

- You have the Repeater with a valid ID ‘REPEATER’. See [Managing Repeaters](/docs/on-premises-repeater-local-agent) for information about handling the Repeaters.
- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) (`BRIGHT_TOKEN`) with the following scopes: `bot`,<br>`scans : run`,`scan : read`, and `scans : stop`.
- You have downloaded the Node.js plug-in to your Jenkins machine.
- You have created the `BRIGHT_TOKEN` environmental variable on your Jenkins machine.
- You have copied the Bright `PROJECT_ID` on the **Projects** page. If you do not specify the `PROJECT_ID`, the scan will be run under **Default** project. 

### Step-by-step guide

#### STEP 1 - Install the CLI

```bash
sh 'npm install @neuralegion/nexploit-cli -g || true'
```



#### STEP 2 - Activate the repeater

```bash
   PID_REPEATER=$(nexploit-cli repeater --token=${BRIGHT_TOKEN} --id=${REPEATER_ID} &> /dev/null & echo $!)
```



> 📘 Note
> 
> If a valid API token `BRIGHT_TOKEN` and Repeater ID `REPEATER` were not added, then the **Unauthorized access** error appears. Please check your credentials.

> 🚧 Important
> 
> Make sure that the Repeater has an outbound connection to the Bright host depending on its deployment. The Repeater should be connected either to the default **amq.app.brightsec.com** via the AMQ protocol (over TLS) using port 5672 or to your private cloud using the relative port.

#### STEP 2 -  Run (retest) a scan

- If you need to run a new scan with a Crawler,  use the following script: 

```bash
  echo "Start Bright Scan 🏁"
           SCAN_ID=$(nexploit-cli scan:run --token ${BRIGHT_TOKEN} --name "Jenkins Scan with Repeater" --crawler https://brokencrystals.com/ --smart)
           echo "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
```



- If you need to re-test a previous scan with its ID `OLD_SCAN_ID` and API key `BRIGHT_TOKEN`, use the following script:

```bash
echo "Retest a scan"
         NEW_SCAN_ID=$(nexploit-cli scan:retest --token=$BRIGHT_TOKEN $OLD_SCAN_ID;
echo "Scan started $NEW_SCAN_ID";
```



#### STEP 4 -  Poll the results

> 📘 Note
> 
> When polling the scan results, it is recommended to follow the fail-fast principle by using the `breakpoint` command.  See [Bright CLI Command List](/docs/command-list) for a full list of commands you can use in your Jenkins flow.

Poll the scan until it returns some issue, or its time runs out:

```bash
  echo "Wait for issues ⏳\n"
           RESULT=$(nexploit-cli scan:polling --interval 30s --timeout 20m --token $BRIGHT_TOKEN --breakpoint high_issue $SCAN_ID)
```



After that - stop the scan:

```bash
  nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
```



#### STEP 5 -  View the  results

To view the scan results, go to the [Bright app](https://app.neuralegion.com). For the instructions, see [here](https://docs.neuralegion.com/docs/reviewing-scan-details#review-scan-results).

### Complete example

The following example is made up of the steps above and shows how to run a new scan via the Repeater using the Crawler discovery type:

```bash
pipeline {
 agent any
 environment {
   BRIGHT_TOKEN = "$BRIGHT_TOKEN"
   REPEATER_ID = "$REPEATER"
   }
 tools {nodejs "node"}
 stages {
   stage("Install Dep"){
       steps{
          sh 'npm install @neuralegion/nexploit-cli -g || true'
       }
   }
   stage('Start Scan') {
     steps {
         sh '''#!/bin/bash
           echo "Start Repeater 🏁"
           PID_REPEATER=$(nexploit-cli repeater --token=${BRIGHT_TOKEN} --id=${REPEATER_ID} &> /dev/null & echo $!)
           echo "Repeater started PID: $PID_REPEATER\n"
           sleep 10
           echo "Start Bright Scan 🏁"
           SCAN_ID=$(nexploit-cli scan:run --token ${BRIGHT_TOKEN} --repeater ${REPEATER_ID} --name "Jenkins Scan with Repeater" --crawler https://brokencrystals.com/ --smart)
           echo "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
           sleep 10
           echo "Wait for issues ⏳\n"
           RESULT=$(nexploit-cli scan:polling --interval 30s --timeout 20m --token $BRIGHT_TOKEN --breakpoint high_issue $SCAN_ID)
           if [ -z "$RESULT" ]
           then
               echo "Failed to stop scan"
           else
               echo "Stop Scan 🛑"
               nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
           fi
       '''
     }
   }
 }
```



## Example 3. Scan in the repeater mode using the Bright CLI (docker installation)

To apply this option, you need to configure a Docker image inside your pipeline (for example,  by creating a docker-compose file). Once the Docker is configured, you can run the Bright CLI and activate the Repeater using the Repeater ID and Bright API key.   

### Prerequisites

- You have the Repeater with a valid ID ‘REPEATER’. See [Managing Repeaters](/docs/on-premises-repeater-local-agent) for the information about handling the Repeaters.
- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) (`BRIGHT_TOKEN`) with the following scopes: `bot`,<br>`scans : run`,`scan : read`, and `scans : stop`.
- You have downloaded the Node.js plug-in to your Jenkins machine.
- You have created the `BRIGHT_TOKEN` environmental variable on your Jenkins machine.
- You have copied the Bright `PROJECT_ID` on the **Projects** page. If you do not specify the `PROJECT_ID`, the scan will be run under **Default** project. 

### Step-by-step guide

#### STEP 1 - Run the docker container with the repeater

```bash
 sh 'npm install @neuralegion/nexploit-cli -g || true'
          sh 'docker rm $(docker ps --filter status=exited -q)'
          sh 'docker run -d --name "NLRepeater1" neuralegion/repeater:latest repeater --id ${REPEATER} --token ${BRIGHT_TOKEN}'
```



> 📘 Note
> 
> If a valid API token `BRIGHT-TOKEN` and Repeater ID `REPEATER` were not added, then the **Unauthorized access** error appears. Please check your credentials.

> 🚧 Important
> 
> Make sure that the Repeater has an outbound connection to the Bright host depending on its deployment. The Repeater should be connected either to the default **amq.app.brightsec.com** via the AMQ protocol (over TLS) using port 5672 or to your private cloud using the relative port.

#### STEP 2 -  Start a Scan

```bash
      SCAN_ID=$(nexploit-cli scan:run --token ${BRIGHT_TOKEN} --repeater ${REPEATER} --name "Jenkins Scan with Docker" --crawler https://brokencrystals.com/ --smart)
           echo "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
```



#### STEP 3 -  Poll the results

> 📘 Note
> 
> When polling the scan results, it is recommended to follow the fail-fast principle by using the `breakpoint` command.  See [Bright CLI Command List](/docs/command-list) for a full list of commands you can use in your Travis flow.

```bash
echo "Poll for scan results";

# Poll the scan until it returns some issue, or its time runs out
   RESULT=$(nexploit-cli scan:polling --interval 30s --timeout 20m --token $BRIGHT_TOKEN --breakpoint high_issue $SCAN_ID)

# After that - stop the scan
nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
```



#### STEP 4 -  Stop the docker container

```bash
  sh 'docker kill "NLRepeater1"'
         sh 'docker rm $(docker ps --filter status=exited -q)'
```



#### STEP 5 -  View the results

To view the scan results, go to the [Bright app](https://app.neuralegion.com). For the instructions, see [here](https://docs.neuralegion.com/docs/reviewing-scan-details#review-scan-results).

### Complete example

The following example is made up of the steps above and shows how to run a new scan via the Repeater using the Crawler discovery type:

```bash
pipeline {
 agent any
 environment {
   BRIGHT_TOKEN = "$BRIGHT_TOKEN"
   }
 tools {nodejs "node"}
 stages {
   stage("Install Dep"){
       steps{
          sh 'npm install @neuralegion/nexploit-cli -g || true'
          sh 'docker rm $(docker ps --filter status=exited -q)'
          sh 'docker run -d --name "NLRepeater1" neuralegion/repeater:latest repeater --id ${REPEATER} --token ${BRIGHT_TOKEN}'
          sleep 5
       }
   }
   stage('Start Scan') {
     steps {
         sh '''#!/bin/bash
           echo "Start Bright Scan 🏁"
           SCAN_ID=$(nexploit-cli scan:run --token ${BRIGHT_TOKEN} --repeater ${REPEATER} --name "Jenkins Scan with Docker" --crawler https://brokencrystals.com/ --smart)
           echo "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
           sleep 10
           echo "Wait for issues ⏳\n"
           RESULT=$(nexploit-cli scan:polling --interval 30s --timeout 20m --token $BRIGHT_TOKEN --breakpoint high_issue $SCAN_ID)
           if [ -z "$RESULT" ]
           then
               echo "Failed to stop scan"
           else
               echo "Stop Scan 🛑"
               nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
           fi
       '''
     }
   }
   stage('Stop Docker container') {
     steps {
         sh 'docker kill "NLRepeater1"'
         sh 'docker rm $(docker ps --filter status=exited -q)'
        }
   }
 }
}

 
```