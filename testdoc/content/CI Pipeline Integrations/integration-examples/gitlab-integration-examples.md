---
title: "GitLab Integration Examples"
slug: "gitlab-integration-examples"
excerpt: "This section provides the GitLab integration examples for different use cases. You can also find these examples directly in the [Bright GitLab repository](https://gitlab.com/neuralegion/nexploit-cicd)."
hidden: false
metadata: 
  description: "To apply this option, you only need to install the NeuraLegion CLI globally on your GitLab machine using the relative NPM command."
createdAt: "2021-09-16T11:49:58.212Z"
updatedAt: "2022-12-08T13:19:51.314Z"
---
## Example 1. Scan from the cloud using the Bright CLI (NPM installation)

To apply this option, you only need to install the <<glossary:Bright CLI>> globally on your GitLab machine using the relative NPM command. 

### Prerequisites

- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) (`BRIGHT_TOKEN`) with the following scopes: `bot`,<br>`scans : run`,`scan : read`, and `scans : stop`.
- You have set the `BRIGHT_TOKEN` variable in your GitLab pipeline: Settings > CI/CD > Variables.
- You have copied the Bright `PROJECT_ID` on the **Projects** page. 

### Step-by-step guide

#### STEP 1 - Install the CLI

```bash
- npm install @neuralegion/nexploit-cli -g --unsafe-perm || true
```



#### STEP 2 -  Run (retest) a scan

- If you need to run a new scan with a Crawler,  use the following script: 

```bash
- echo "Start Bright Scan 🏁"
  - >
    SCAN_ID=$(nexploit-cli scan:run --token $BRIGHT_TOKEN
    --name "Test Gitlab Scan"
    --project $PROJECT_ID
    --crawler www.example.com 
    --smart)
  - echo "export SCAN_ID=$SCAN_ID" > $CI_PROJECT_DIR/variables
  - printf "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
```



- If you need to re-test a previous scan with its ID `OLD_SCAN_ID`, use the following script:

```bash
- echo "Retest a scan"
- >
  NEW_SCAN_ID=$(nexploit-cli scan:retest --token=$BRIGHT_TOKEN $OLD_SCAN_ID)
-printf "Scan was started with ID https://app.brightsec.com/scans/$NEW_SCAN_ID\n"
```



#### STEP 3 -  Poll the results

> 📘 Note
> 
> When polling the scan results, it is recommended to follow the fail-fast principle by using the `breakpoint` command.  See [Bright CLI Command List](/docs/command-list) for a full list of commands you can use in your GitLab flow.

```bash
- printf "Wait for issues ⏳\n"

 - >
  # Poll the scan until it returns something, or its time runs out
  (nexploit-cli scan:polling
    --interval 30s
    --timeout 20m
    --token $BRIGHT_TOKEN
    --breakpoint medium_issue $SCAN_ID)
  artifacts:
    paths:
    - variables
  allow_failure: true

# After that - stop the scan
 echo "Stop Scan 🛑"
      nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
```



#### STEP 4 - View the results

To view the scan results, go to the [Bright app](https://app.brightsec.com). For the instructions, see [here](/docs/reviewing-scan-details#review-scan-results). 

> 👍 Tip
> 
> You can also configure a script to get the scan results directly in the job output. The configuration sample in given in **Example 4**.

### Complete example

The following example is made up of the steps above and shows how to run a new scan using the Crawler discovery type:

```bash
language: node_js
node_js:
 - 10
before_script:
 - npm install @neuralegion/nexploit-cli -g || true
script:
 - printf "Start Bright Scan 🏁"
 - >
  SCAN_ID=$(nexploit-cli scan:run
  --token $BRIGHT_TOKEN
  --name "Test Travis Scan"
  --project $PROJECT_ID
  --crawler http://brokencrystals.com
  --smart)
 - printf "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
 - printf "Wait for issues ⏳\n"
 - >
   nexploit-cli scan:polling
   --interval 30s
   --timeout 20m
   --token $BRIGHT_TOKEN
   --breakpoint medium_issue $SCAN_ID
allow_failure: true
after_script:
 - printf "Stop Scan 🛑"
 - nexploit-cli scan:stop 
 --token $BRIGHT_TOKEN $SCAN_IDimage: ubuntu:20.04
cache:
  paths:
  - variables
test:
  before_script:
  - apt update -qq --fix-missing
  - apt install -y --no-install-recommends nodejs npm make g++
  - npm install @neuralegion/nexploit-cli -g --unsafe-perm || true
  script:
  - echo "Start Bright Scan 🏁"
  - >
    SCAN_ID=$(nexploit-cli scan:run --token $BRIGHT_TOKEN
    --name "Test Gitlab Scan"
    --project $PROJECT_ID
    --crawler https://juice-shop.herokuapp.com/
    --smart)
  - echo "export SCAN_ID=$SCAN_ID" > $CI_PROJECT_DIR/variables
  - printf "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
  - printf "Wait for issues ⏳\n"
  - >
    (nexploit-cli scan:polling
    --interval 30s
    --timeout 20m
    --token $BRIGHT_TOKEN
    --breakpoint medium_issue $SCAN_ID)
  artifacts:
    paths:
    - variables
  allow_failure: true
  after_script:
  - source $CI_PROJECT_DIR/variables
  - >
    if [ -e $CI_PROJECT_DIR/variables ]; then
      echo "Stop Scan 🛑"
      nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
    else
      echo "Failed to stop scan"
    fi
```



## Example 2. Scan in the Repeater mode using the Bright CLI (NPM installation)

To apply this option, you need to install the Bright CLI on your GitLab machine and activate the Repeater using the Repeater ID and Bright API key. 

### Prerequisites

- You have the Repeater with a valid ID ‘REPEATER’. See [Managing Repeaters](/docs/on-premises-repeater-local-agent) for the information about handling the Repeaters.
- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) (`BRIGHT_TOKEN`) with the following scopes: `bot`,<br>`scans : run`,`scan : read`, and `scans : stop`.
- You have set the `BRIGHT_TOKEN` and `REPEATER` variables in your GitLab pipeline: Settings > CI/CD > Variables.
- You have copied the Bright `PROJECT_ID` on the **Projects** page. 

### Step-by-step guide

#### STEP 1 - Install the CLI

```bash
- npm install @neuralegion/nexploit-cli -g --unsafe-perm || true
```



#### STEP 2 - Activate the repeater

```bash
- echo "Run repeater 🔁"
  - echo $REPEATER
  - echo $BRIGHT_TOKEN
  - >
    nexploit-cli repeater
    --token $BRIGHT_TOKEN
    --id $REPEATER
```



> 📘 Note
> 
> If a valid API token `BRIGHT_TOKEN` and Repeater ID `REPEATER` were not added, then the **Unauthorized access** error appears. Please check your credentials.

> 🚧 Important
> 
> Make sure that the Repeater has an outbound connection to the Bright host depending on its deployment. The Repeater should be connected either to the default **amq.app.brightsec.com** via the AMQ protocol (over TLS) using port 5672 or to your private cloud using the relative port.

#### STEP 3 -  Run (retest) a scan

- If you need to run a new scan with a Crawler,  use the following script: 

```bash
- echo "Start Bright Scan 🏁"
  - >
    SCAN_ID=$(nexploit-cli scan:run --token $BRIGHT_TOKEN
    --name "Test Gitlab Scan"
    --project $PROJECT_ID
    --repeater $REPEATER
    --crawler www.example.com 
    --smart)
  - echo "export SCAN_ID=$SCAN_ID" > $CI_PROJECT_DIR/variables
  - printf "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
```



- If you need to re-test a previous scan with its ID `OLD_SCAN_ID`, use the following script:

```bash
- echo "Retest a scan"
- >
  NEW_SCAN_ID=$(nexploit-cli scan:retest --token=$BRIGHT_TOKEN $OLD_SCAN_ID)
-printf "Scan was started with ID https://app.brightsec.com/scans/$NEW_SCAN_ID\n"
```



#### STEP 4 -  Poll the results

> 📘 Note
> 
> When polling the scan results, it is recommended to follow the fail-fast principle by using the `breakpoint` command.  See [Bright CLI Command List](/docs/command-list) for a full list of commands you can use in your GitLab flow.

```bash
- printf "Wait for issues ⏳\n"

 - >
  # Poll the scan until it returns something, or its time runs out
  (nexploit-cli scan:polling
    --interval 30s
    --timeout 20m
    --token $BRIGHT_TOKEN
    --breakpoint medium_issue $SCAN_ID)
  artifacts:
    paths:
    - variables
  allow_failure: true

# After that - stop the scan
 echo "Stop Scan 🛑"
      nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
```



#### STEP 5 -  View the results

To view the scan results, go to the [Bright app](https://app.brightsec.com). For the instructions, see [here](/docs/reviewing-scan-details#review-scan-results). 

> 👍 Tip
> 
> You can also configure a script to get the scan results directly in the job output. The configuration sample in given in Example 4.

### Complete example

The following example is made up of the steps above and shows how to run a new scan using the Crawler discovery type:

```bash
image: ubuntu:20.04
cache:
  paths:
  - variables
test:
  before_script:
  - apt update -qq --fix-missing
  - apt install -y --no-install-recommends nodejs npm make g++
  - npm install @neuralegion/nexploit-cli -g --unsafe-perm || true
  script:
  - echo "Run repeater 🔁"
  - echo $REPEATER
  - echo $BRIGHT_TOKEN
  - >
    nexploit-cli repeater
    --token $BRIGHT_TOKEN
    --id $REPEATER
  - echo "Start Bright Scan 🏁"
  - >
    SCAN_ID=$(nexploit-cli scan:run --token $BRIGHT_TOKEN
    --repeater $REPEATER
    --name "Test Gitlab Scan"
    --project $PROJECT_ID
    --crawler https://brokencrystals.com
    --smart)
  - echo "export SCAN_ID=$SCAN_ID" > $CI_PROJECT_DIR/variables
  - printf "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
  - printf "Wait for issues ⏳\n"
  - >
    (nexploit-cli scan:polling
    --interval 30s
    --timeout 20m
    --token $BRIGHT_TOKEN
    --breakpoint medium_issue $SCAN_ID)
  artifacts:
    paths:
    - variables
  allow_failure: true
  after_script:
  - source $CI_PROJECT_DIR/variables
  - >
    if [ -e $CI_PROJECT_DIR/variables ]; then
      echo "Stop Scan 🛑"
      nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
    else
      echo "Failed to stop scan"
    fi
```



## Example 3. Scan in the repeater mode using the Bright CLI (Docker installation)

To apply this option, you need to configure a Docker image inside your pipeline (for example,  by creating a docker-compose file). Once the Docker is configured, you can run the Bright CLI and activate the Repeater using the Repeater ID and Bright API key.   

### Prerequisites

- You have the Repeater with a valid ID ‘REPEATER’. See [Managing Repeaters](/docs/on-premises-repeater-local-agent) for the information about handling the Repeaters.
- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) (`BRIGHT_TOKEN`) with the following scopes: `bot`,<br>`scans : run`,`scan : read`, and `scans : stop`.
- You have set the `BRIGHT_TOKEN` and `REPEATER` variables in your GitLab pipeline: Settings > CI/CD > Variables.
- You have copied the Bright `PROJECT_ID` on the **Projects** page. 

### Step-by-step guide

#### STEP 1 - Create the Docker compose `yml` file

```bash
version: '3'
services:
  juiceshop.local:
    image: bkimminich/juice-shop
    ports:
          - "3000:3000"
  repeater:
    image: neuralegion/repeater:latest
    restart: always
    environment:
      REPEATER_TOKEN: $BRIGHT_TOKEN
      REPEATER_AGENT: $REPEATER
      DEBUG: nexploit-cli
```



#### STEP 2 - Deploy the Docker and run the CLI

```bash
before_script:
  - touch variables.txt
  - echo "****** INSTALL DEPENDECIES *********"
  - apt-get update
  - apt-get -y install curl
  - curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
  - chmod +x /usr/local/bin/docker-compose
  - apt-get -y install apt-transport-https ca-certificates curl software-properties-common
  - curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
  - add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
  - apt update
  - apt-cache policy docker-ce
  - apt-get -y install docker-ce
  - docker-compose --version
  - service docker start
  - apt update -qq --fix-missing
  - apt install -y --no-install-recommends nodejs npm make g++
  - npm install @neuralegion/nexploit-cli -g --unsafe-perm || true
script:
  - echo "Start docker-compose configuration"
  - docker-compose up --detach
  - sleep 5s
```



#### STEP 3 -  Run (retest) a scan

- If you need to run a new scan with a Crawler, use the following script: 

```bash
- echo "Start Bright Scan 🏁"
  - >
    SCAN_ID=$(nexploit-cli scan:run --token $BRIGHT_TOKEN
    --name "Test Gitlab Scan"
    --project $PROJECT_ID
    --repeater $REPEATER
    --crawler www.example.com 
    --smart)
  - echo "export SCAN_ID=$SCAN_ID" > $CI_PROJECT_DIR/variables
  - printf "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
```



- If you need to re-test a previous scan with its ID `OLD_SCAN_ID`, use the following script:

```bash
- echo "Retest a scan"
- >
  NEW_SCAN_ID=$(nexploit-cli scan:retest --token=$BRIGHT_TOKEN $OLD_SCAN_ID)
-printf "Scan was started with ID https://app.brightsec.com/scans/$NEW_SCAN_ID\n"
```



#### STEP 4 -  Poll the results

> 📘 Note
> 
> When polling the scan results, it is recommended to follow the fail-fast principle by using the `breakpoint` command.  See [Bright CLI Command List](/docs/command-list) for a full list of commands you can use in your GitLab flow.

```bash
- printf "Wait for issues ⏳\n"

 - >
  # Poll the scan until it returns something, or its time runs out
  (nexploit-cli scan:polling
    --interval 30s
    --timeout 20m
    --token $BRIGHT_TOKEN
    --breakpoint medium_issue $SCAN_ID)
  artifacts:
    paths:
    - variables
  allow_failure: true

# After that - stop the scan
 echo "Stop Scan 🛑"
      nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
```



#### STEP 5 -  View the results

To view the scan results, go to the [Bright app](https://app.neuralegion.com). For the instructions, see [here](/docs/reviewing-scan-details#review-scan-results). 

> 👍 Tip
> 
> You can also configure a script to get the scan results directly in the job output. The configuration sample in given in Example 4.

### Complete example

The following example is made up of the steps above and shows how to run a new scan using the Crawler discovery type:

```bash
image: ubuntu:20.04
cache:
  paths:
  - variables
test:
  before_script:
  - touch variables.txt
  - echo "****** INSTALL DEPENDECIES *********"
  - apt-get update
  - apt-get -y install curl
  - curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
  - chmod +x /usr/local/bin/docker-compose
  - apt-get -y install apt-transport-https ca-certificates curl software-properties-common
  - curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -
  - add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"
  - apt update
  - apt-cache policy docker-ce
  - apt-get -y install docker-ce
  - docker-compose --version
  - service docker start
  - apt update -qq --fix-missing
  - apt install -y --no-install-recommends nodejs npm make g++
  - npm install @neuralegion/nexploit-cli -g --unsafe-perm || true
  script:
  - echo "Start docker-compose configuration"
  - docker-compose up --detach
  - sleep 5s
  - echo "Start Bright Scan 🏁"
  - >
    SCAN_ID=$(nexploit-cli scan:run --token $BRIGHT_TOKEN
    --repeater $REPEATER
    --name "Test Gitlab Scan"
    --project $PROJECT_ID
    --crawler http://juiceshop.local:3000
    --smart)
  - echo "export SCAN_ID=$SCAN_ID" > $CI_PROJECT_DIR/variables
  - printf "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
  - printf "Wait for issues ⏳\n"
  - >
    (nexploit-cli scan:polling
    --interval 30s
    --timeout 20m
    --token $BRIGHT_TOKEN
    --breakpoint medium_issue $SCAN_ID)
  artifacts:
    paths:
    - variables
  allow_failure: true
  after_script:
  - source $CI_PROJECT_DIR/variables
  - >
    if [ -e $CI_PROJECT_DIR/variables ]; then
      echo "Stop Scan 🛑"
      nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
    else
      echo "Failed to stop scan"
    fi
```



## Example 4. Run a scan and view the results in the job output

The script below is configured to run a scan from the Bright cloud and send the details of all detected issues (vulnerabilities) directly to the job output. You can combine this script with the scripts given in the examples below to take maximum advantage of scanning.  

### Prerequisites

- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) (`BRIGHT_TOKEN`) with the following scopes: `bot`,<br>`scans : run`,`scan : read`, and `scans : stop`.
- You have set the `BRIGHT_TOKEN` variable in your GitLab pipeline: Settings > CI/CD > Variables.
- You have copied the Bright `PROJECT_ID` on the **Projects** page. 

### Complete example

```bash
image: ubuntu:20.04
cache:
  paths:
  - variables
test:
  before_script:
  - apt update -qq --fix-missing
  - apt install -y --no-install-recommends nodejs npm make g++
  - npm install @neuralegion/nexploit-cli -g --unsafe-perm || true
  - apt install jq -y
  - apt install curl -y
  script:
  - echo "Start Bright Scan 🏁"
  - >
    SCAN_ID=$(nexploit-cli scan:run --token $BRIGHT_TOKEN
    --name "GitLab Integration Scan"
    --project $PROJECT_ID
    --crawler https://brokencrystals.com
    --smart)
  - echo "export SCAN_ID=$SCAN_ID" > $CI_PROJECT_DIR/variables
  - printf "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
  - printf "Wait for issues ⏳\n"
  - >
    (nexploit-cli scan:polling
    --interval 30s
    --timeout 20m
    --token $BRIGHT_TOKEN
    --breakpoint high_issue $SCAN_ID)
  artifacts:
    paths:
    - variables
  allow_failure: true
  after_script:
  - source $CI_PROJECT_DIR/variables
  - >
    if [ -e $CI_PROJECT_DIR/variables ]; then
      echo "Stop Scan 🛑"
      nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
    else
      echo "Failed to stop scan"
    fi
          sleep 10
              #We send a curl request to get all the scan issues and after that we parse the Id with jq
                GET_ID=$(curl -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H          'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].id' )
                #We delete "(quotation marks) and insert all ids into the new array  
                ISSUES_ID_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_ID")
                #We insert everything from a previously made array into a new array(a), and for each value we give index value
                a=(); while read -r line; do a+=("$line"); done <<<"$ISSUES_ID_ARRAY"; declare a;

                GET_NAME=$(curl -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].name' )
                ISSUES_NAME_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_NAME")
                b=(); while read -r line; do b+=("$line"); done <<<"$ISSUES_NAME_ARRAY"; declare b;

                GET_DETAILS=$(curl -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].details' )
                ISSUES_DETAILS_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_DETAILS")
                c=(); while read -r line; do c+=("$line"); done <<<"$ISSUES_DETAILS_ARRAY"; declare c;

                GET_SEVERITY=$(curl -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].severity' )
                ISSUES_SEVERITY_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_SEVERITY")
                d=(); while read -r line; do d+=("$line"); done <<<"$ISSUES_SEVERITY_ARRAY"; declare d;

                GET_PROTOCOL=$(curl -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].protocol' )
                ISSUES_PROTOCOL_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_PROTOCOL")
                e=(); while read -r line; do e+=("$line"); done <<<"$ISSUES_PROTOCOL_ARRAY"; declare e;

                GET_EXPOSURE=$(curl -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].exposure' )
                ISSUES_EXPOSURE_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_EXPOSURE")
                f=(); while read -r line; do f+=("$line"); done <<<"$ISSUES_EXPOSURE_ARRAY"; declare f;

                GET_CVSS=$(curl -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].cvss' )
                ISSUES_CVSS_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_CVSS")
                g=(); while read -r line; do g+=("$line"); done <<<"$ISSUES_CVSS_ARRAY"; declare g;

                GET_CWE=$(curl -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].cwe' )
                ISSUES_CWE_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_CWE")
                h=(); while read -r line; do h+=("$line"); done <<<"$ISSUES_CWE_ARRAY"; declare h;

                GET_TIME=$(curl -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].time' )
                ISSUES_TIME_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_TIME")
                j=(); while read -r line; do i+=("$line"); done <<<"$ISSUES_TIME_ARRAY"; declare j;

      echo "The number of issues we found is ${#a[*]}"
      len=${#a[*]}
      i=0
      while [ $i -lt $len ]; do
        echo " "
        echo " "
        echo "ID OF THE SCAN IS    ${a[$i]}"
        echo "NAME    "${b[$i]}
        echo "DETAILS    "${c[$i]}
        echo "SEVERITY    "${d[$i]}
        echo "PROTOCOL    "${e[$i]}
        echo "EXPOSURE    "${f[$i]}
        echo "CVSS    "${g[$i]}
        echo "CWE    "${h[$i]}
        echo "TIME    "${j[$i]}
        let i=i+1
      done
```