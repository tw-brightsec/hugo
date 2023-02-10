---
title: "Travis CI Integration Examples"
slug: "travis-ci-integration-examples"
excerpt: "This section provides the Travis CI integration examples for different use cases."
hidden: false
metadata: 
  description: "To apply this option, you only need to install the NeuraLegion CLI globally on your Travis CI machine using the relative NPM command."
createdAt: "2021-09-16T10:43:12.425Z"
updatedAt: "2022-12-08T13:08:51.481Z"
---
## Example 1. Scan from the cloud using the Bright CLI (NPM installation)

To apply this option, you only need to install the Bright CLI globally on your Travis CI machine using the relative NPM command. 

### Prerequisites

- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) (`BRIGHT_TOKEN`) with the following scopes: `bot`,<br>`scans : run`,`scan : read`, and `scans : stop`.
- You have created the `BRIGHT_TOKEN` variable on your Travis CI machine: more options > settings > add the environmental variable.
- You have copied the Bright `PROJECT_ID` on the **Projects** page. 

### Step-by-step guide

#### STEP 1 - Install the CLI

```bash
- npm install @neuralegion/bright-cli -g || true
```



#### STEP 2 -  Run (retest) a scan

- If you need to run a new scan with a Crawler,  use the following script: 

```bash
-printf "Start Bright Scan 🏁"
- >
SCAN_ID=$(bright-cli scan:run 
 --token $BRIGHT_TOKEN
 --name "Test Travis Scan" 
 --project $PROJECT_ID
 --crawler www.example.com 
 --smart)
- printf "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
```



- If you need to re-test a previous scan with its ID `OLD_SCAN_ID`, use the following script:

```bash
-printf "Retest a scan"
- >
NEW_SCAN_ID=$(bright-cli scan:retest 
 --token=$BRIGHT_TOKEN
 $OLD_SCAN_ID)
-printf "Scan was started with ID https://app.brightsec.com/scans/$NEW_SCAN_ID\n"
```



#### STEP 3 -  Poll the results

> 📘 Note
> 
> When polling the scan results, it is recommended to follow the fail-fast principle by using the `breakpoint` command.  See [Bright CLI Command List](/docs/command-list) for a full list of commands you can use in your Travis flow.

```bash
- printf "Wait for issues ⏳\n"

 - >
  # Poll the scan until it returns something, or its time runs out
  nexploit-cli scan:polling 
   --interval 30s 
   --timeout 20m
   --token $BRIGHT_TOKEN
   --breakpoint medium_issue 
   $SCAN_ID

allow_failure: true

# After that - stop the scan
 - printf "Stop Scan 🛑"
 - nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID

```



#### STEP 4 -  View the results

To view the scan results, go to the [Bright app](https://app.neuralegion.com). For the instructions, see [here](https://docs.neuralegion.com/docs/reviewing-scan-details#review-scan-results).

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
  SCAN_ID=$(bright-cli scan:run
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
 --token $BRIGHT_TOKEN $SCAN_ID
```



## Example 2. Scan in the Repeater mode using the Bright CLI (NPM installation)

To apply this option, you need to install the Bright CLI on your Travis CI machine and activate the Repeater using the Repeater ID and Bright API key. 

### Prerequisites

- You have the Repeater with a valid ID ‘REPEATER’. See [Managing Repeaters](/docs/on-premises-repeater-local-agent) for the information about handling the Repeaters.
- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) (`BRIGHT_TOKEN`) with the following scopes: `bot`,<br>`scans : run`,`scan : read`, and `scans : stop`.
- You have created the `BRIGHT_TOKEN` and `REPEATER` variables on your Travis CI machine: more options > settings > add the environmental variables.
- You have copied the Bright `PROJECT_ID` on the **Projects** page. 

### Step-by-step guide

#### STEP 1 - Install the CLI

```bash
- npm install @neuralegion/nexploit-cli -g || true
```



#### STEP 2 - Activate the repeater

```bash
nexploit-cli repeater 
--token $BRIGHT_TOKEN 
--id $REPEATER 
--cluster https://app.brightsec.com 
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
-printf "Start Bright Scan 🏁"
- >
SCAN_ID=$(bright-cli scan:run 
--token $BRIGHT_TOKEN
--name "Test Travis Scan" 
--project $PROJECT_ID
--repeater $REPEATER
--crawler www.example.com 
--smart) 
- printf "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
```



- If you need to re-test a previous scan with its ID `OLD_SCAN_ID`, use the following script:

```bash
-printf "Retest a scan"
- >
NEW_SCAN_ID=$(bright-cli scan:retest 
--token=$BRIGHT_TOKEN 
$OLD_SCAN_ID)
-printf "Scan was started with ID https://app.brightsec.com/scans/$NEW_SCAN_ID\n"
```



#### STEP 4 -  Poll the results

> 📘 Note
> 
> When polling the scan results, it is recommended to follow the fail-fast principle by using the `breakpoint` command.  See [Bright CLI Command List](/docs/command-list) for a full list of commands you can use in your Travis flow.

```bash
- printf "Wait for issues ⏳\n"
 - >
# Poll the scan until it returns something, or its time runs out
nexploit-cli scan:polling 
--interval 30s 
--timeout 20m
--token $BRIGHT_TOKEN
--breakpoint medium_issue $SCAN_ID
allow_failure: true

# After that - stop the scan
 - printf "Stop Scan 🛑"
 - nexploit-cli scan:stop 
 --token $BRIGHT_TOKEN $SCAN_ID

```



#### STEP 5 -  View the results

To view the scan results, go to the [Bright app](https://app.neuralegion.com). For the instructions, see [here](https://docs.neuralegion.com/docs/reviewing-scan-details#review-scan-results).

### Complete example

The following example is made up of the steps above and shows how to run a new scan using the Crawler discovery type:

```bash
language: node_js
node_js:
 - 10
before_script:
 - npm install @neuralegion/nexploit-cli -g || true
script:
  nexploit-cli repeater 
  --token $BRIGHT_TOKEN
  --id $REPEATER 
  --bus amqps://amq.app.brightsec.com:5672 
 - printf "Start Bright Scan 🏁"
 - >
  SCAN_ID=$(nexploit-cli scan:run
  --token $BRIGHT_TOKEN
  --name "Test Travis Scan"
  --project $PROJECT_ID
  --repeater $REPEATER
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
 --token $BRIGHT_TOKEN $SCAN_ID
```



## Example 3. Scan in the Repeater mode using the Bright CLI (Docker installation)

To apply this option, you need to configure a Docker image inside your pipeline (for example, by creating a docker-compose file). Once the Docker is configured, you can run the Bright CLI and activate the Repeater using the Repeater ID and Bright API key.   

### Prerequisites

- You have the Repeater with a valid ID ‘REPEATER’. See [Managing Repeaters](/docs/on-premises-repeater-local-agent) for the information about handling the Repeaters.
- You have a valid [organization API key](/docs/manage-your-organization#manage-organization-apicli-authentication-tokens) or [personal API key](/docs/manage-your-personal-account#manage-your-personal-api-keys-authentication-tokens) (`BRIGHT_TOKEN`) with the following scopes: `bot`,<br>`scans : run`,`scan : read`, and `scans : stop`.
- You have created the `BRIGHT_TOKEN` and `REPEATER` variables on your Travis CI machine: more options > settings > add the environmental variables.
- You have copied the Bright `PROJECT_ID` on the **Projects** page. 

### Step-by-step guide

#### STEP 1 - Create the Docker compose `yml` file

```bash
version:'3'
services:
 brokencrystals.local:
  image: neuralegion/brokencrystals
 repeater:
  image: neuralegion/repeater:latest
  restart: always
  environment:
   REPEATER_TOKEN: ${BRIGHT_TOKEN}
   REPEATER_AGENT: ${REPEATER}
   DEBUG: nexploit-cli
```



#### STEP 2 - Deploy the Docker and run the CLI

```bash
- sudo curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
- sudo chmod +x /usr/local/bin/docker-compose
- npm install @neuralegion/nexploit-cli -g || true
```



#### STEP 3 - Activate the repeater

```bash
- - printf "BRIGHT_TOKEN=$BRIGHT_TOKEN\nREPEATER=$REPEATER\n" > .env
- cat .env
- docker-compose --env-file=.env up -d
- docker-compose config
```



> 📘 Note
> 
> If a valid API token `BRIGHT_TOKEN` and Repeater ID `REPEATER` were not added, then the **Unauthorized access** error appears. Please check your credentials.

> 🚧 Important
> 
> Make sure that the Repeater has an outbound connection to the Bright host depending on its deployment. The Repeater should be connected either to the default **amq.app.brightsec.com** via the AMQ protocol (over TLS) using port 5672 or to your private cloud using the relative port.

#### STEP 4 -  Run (retest) a scan

- If you need to run a new scan with a Crawler,  use the following script: 

```bash
-printf "Start Bright Scan 🏁"
- >
SCAN_ID=$(bright-cli scan:run 
--token $BRIGHT_TOKEN
--name "Test Travis Scan"
--project $PROJECT_ID 
--repeater $REPEATER
--crawler www.example.local 
--smart) 
- printf "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
```



- If you need to re-test a previous scan with its ID `OLD_SCAN_ID`, use the following script:

```bash
-printf "Retest a scan"
- >
NEW_SCAN_ID=$(bright-cli scan:retest 
--token=$BRIGHT_TOKEN 
$OLD_SCAN_ID)
-printf "Scan was started with ID https://app.brightsec.com/scans/$NEW_SCAN_ID\n"
```



#### STEP 5 -  Poll the results

> 📘 Note
> 
> When polling the scan results, it is recommended to follow the fail-fast principle by using the `breakpoint` command.  See [Bright CLI Command List](/docs/command-list) for a full list of commands you can use in your Travis flow.

```bash
- printf "Wait for issues ⏳\n"
 - >
# Poll the scan until it returns something, or its time runs out
nexploit-cli scan:polling 
--interval 30s 
--timeout 20m
--token $BRIGHT_TOKEN
--breakpoint medium_issue $SCAN_ID
allow_failure: true

# After that - stop the scan
 - printf "Stop Scan 🛑"
 - nexploit-cli scan:stop 
 --token $BRIGHT_TOKEN $SCAN_ID

```



#### STEP 6 -  View the results

To view the scan results, go to the [Bright app](https://app.brightsec.com). For the instructions, see [here](https://docs.brightsec.com/docs/reviewing-scan-details#review-scan-results).

### Complete example

The following example is made up of the steps above and shows how to run a new scan using the Crawler discovery type:

```bash
language: node_js
node_js:
 - 10
before_script:
 - sudo curl -L "https://github.com/docker/compose/releases/download/1.26.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
 - sudo chmod +x /usr/local/bin/docker-compose
 - npm install @neuralegion/nexploit-cli -g || true
script:
 - printf "BRIGHT_TOKEN=$BRIGHT_TOKEN\nREPEATER=$REPEATER\n" > .env
 - cat .env
 - docker-compose --env-file=.env up -d
 - docker-compose config
 - printf "Start Bright Scan 🏁"
 - >
  SCAN_ID=$(nexploit-cli scan:run
  --token $BRIGHT_TOKEN
  --repeater $REPEATER
  --name "Test Travis Scan"
  --project $PROJECT_ID
  --crawler http://brokencrystals.local
  --smart)
 - printf "Scan was started with ID https://app.brightsec.com/scans/$SCAN_ID\n"
 - printf "Wait for issues ⏳\n"
 - >
   (nexploit-cli scan:polling
   --interval 30s
   --timeout 20m
   --token $BRIGHT_TOKEN
   --breakpoint medium_issue $SCAN_ID
allow_failure: true
after_script:
 - printf "Stop Scan 🛑"
 - nexploit-cli scan:stop 
 --token $BRIGHT_TOKEN $SCAN_ID
```