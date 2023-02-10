---
title: "Sending Detected Issues from CI/CD Pipelines to Jira"
slug: "sending-detected-issues-to-jira-from-cicd-pipelines"
hidden: false
createdAt: "2022-04-16T14:11:51.828Z"
updatedAt: "2022-12-08T12:33:25.809Z"
---
You can configure your CI/CD pipeline to automatically run a Bright scan on every new build and check if a detected issue (vulnerability) is newly occurring or repeated. If the issue is new, Bright will send the details to Jira to open a corresponding issue ticket. 

To integrate your CI/CD pipeline with Bright to automatically run a scan on every new build, see [Integrate Bright with Your CI Pipeline](/docs/integrate-nexploit-with-your-ticketing-system).

In this section, you will find the instructions on how to configure a script to check if a detected issue was found previously and only send new issues to Jira. Additionally, you can also send custom fields to Jira using the provided example. 

## Prerequisites

1. You have already configured the integration of your CI/CD pipeline with Bright. For more information, see [Integrate Bright with Your CI Pipeline](/docs/integrate-nexploit-with-your-ticketing-system).
2. You have copied the ID of the Project under which you are going to run scans (PROJECT_ID). You can find it on the **Projects** page of the [Bright app](https://app.neuralegion.com).
3. You have copied the ID of the scan (SCAN_ID) which is run from the pipeline. You can find it on the **Scans** page of the [Bright app](https://app.neuralegion.com).

## Step-by-step configuration

In this guide, we are using the Jenkins pipeline as an example.

Here is a fully configured script. Below you will find the step-by-step configuration of it. 

```curl
pipeline {
    agent any
    tools {nodejs "node"}
    stages {
        stage('script') {
            steps {
                sh '''#!/bin/bash
                #First we need to install jq(apt-get install jq)
                jq --version
                SCAN_ID=""
                PROJECT_ID=""
                echo "Scan ID is: " $SCAN_ID
                echo "Project ID is: " $PROJECT_ID
            
                GET_ID=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].id' )
                ISSUES_ID_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_ID")
                a=(); while read -r line; do a+=("$line"); done <<<"$ISSUES_ID_ARRAY"; declare a;
                
                GET_OCCURRENCES=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/projects/'$PROJECT_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].occurrences')
                ISSUES_PROJECT_OCCURRENCES=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_OCCURRENCES")
                l=(); while read -r line; do l+=("$line"); done <<<"$ISSUES_PROJECT_OCCURRENCES"; declare l;
                
                GET_NAME=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].name' )
                ISSUES_NAME_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_NAME")
                b=(); while read -r line; do b+=("$line"); done <<<"$ISSUES_NAME_ARRAY"; declare b;
                
                GET_DETAILS=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].details' )
                ISSUES_DETAILS_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_DETAILS")
                c=(); while read -r line; do c+=("$line"); done <<<"$ISSUES_DETAILS_ARRAY"; declare c;
                
                GET_SEVERITY=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].severity' )
                ISSUES_SEVERITY_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_SEVERITY")
                d=(); while read -r line; do d+=("$line"); done <<<"$ISSUES_SEVERITY_ARRAY"; declare d;
                
                GET_EXPOSURE=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].exposure' )
                ISSUES_EXPOSURE_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_EXPOSURE")
                f=(); while read -r line; do f+=("$line"); done <<<"$ISSUES_EXPOSURE_ARRAY"; declare f;
                
                GET_CVSS=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].cvss' )
                ISSUES_CVSS_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_CVSS")
                g=(); while read -r line; do g+=("$line"); done <<<"$ISSUES_CVSS_ARRAY"; declare g; 

                GET_CWE=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].cwe' )
                ISSUES_CWE_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_CWE")
                h=(); while read -r line; do h+=("$line"); done <<<"$ISSUES_CWE_ARRAY"; declare h;
                
                GET_REMEDY=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].remedy' )
                ISSUES_REMEDY_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_REMEDY")
                r=(); while read -r line; do r+=("$line"); done <<<"$ISSUES_REMEDY_ARRAY"; declare r;
                
                GET_TIME=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].time' )
                ISSUES_TIME_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_TIME")
                s=(); while read -r line; do s+=("$line"); done <<<"$ISSUES_TIME_ARRAY"; declare s;
                
                GET_PROJECTISSUES=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/projects/'$PROJECT_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'')
    
                echo "We found ${#a[*]} vulnerabilities in this scan"
                echo "We found  ${#l[*]} issues in this project and now we will filter them and send just new vulnerabilities to Jira"
                len=${#a[*]}
                i=0
                k=0
                while [ $i -lt $len ]; do
                    while [ $k -lt ${#l[*]} ]; do
                        declare -A new=([$k]="$GET_PROJECTISSUES")
                        ISSUES_PROJECT=$(sed -e 's/^"//' -e 's/"$//' <<<${new[$k]} | jq '.['$k'].issueIds')
                        o=(); while read -r line; do o+=("$line"); done <<<"$ISSUES_PROJECT"; declare o;
                        if [[ " ${o[*]} " =~ "${a[$i]}" ]]; then
                            if [[ ${l[$k]} -lt 2 ]]; then
                                echo "____________________________________________________________________________________"
                                echo "We have found this issue " ${b[$i]} ${l[$k]} " times in thid part of the website, so we will send it to the Jira."
                                echo "____________________________________________________________________________________"
                                jiraPost=$(curl -X 'POST' 'http://192.168.56.1:8086/rest/api/2/issue/' -u 'testing:testing' --data '{
                                                                                                                      "fields": {
                                                                                                                                "project":
                                                                                                                                        {
                                                                                                                                        "key": "JEN"
                                                                                                                                        },
                                                                                                                                        "summary": "'"${b[$i]}"'",
                                                                                                                                        "description": "DETAILS: '"${c[$i]}"',\\nDISCOVERED: '"${s[$i]}"',\\nSEVERITY: '"${d[$i]}"',\\nEXPOSURE: '"${f[$i]}"',\\nREMEDY: '"${r[$i]}"',\\nCVSS: '"${g[$i]}"',\\nCWE: '"${h[$i]}"'", 
                                                                                                                                        "issuetype": {
                                                                                                                                                     "name": "Task"
                                                                                                                                                     },
                                                                                                                                                     "customfield_10300": "Some Custom Value"
                                                                                                                                                }
                                                                                                                                            }' -H "Content-Type: application/json")
                                echo $jiraPost
                            else
                                echo "We have found this issue " ${b[$i]} ${l[$k]} " times in this part of the website, so we will not send it to Jira"
                            fi
                        fi
                    let k++
                    done
                let i++
                k=0
                done
                 '''
            }
        }
    }
}
```



1. The first thing you need to do is to install `jq`. For that, use the `apt install jq` command.
2. Validate the installation. For that, type `jq --version` in your Jenkins pipeline and see if you can get the version from `jq`.
3. If you are going to run the script inside a scan (which is the best option), you only need to specify the PROJECT_ID that you used before for the scans against the same target and that you are currently using. Because when an issue is found during the scan, Bright will check if the same issue has been found previously in the project you defined. If the issue has already been found,  Bright will not send it to Jira. But if the issue is newly occurring, a corresponding issue ticket will be created in Jira.  
   If you want to test the script, enter the PROJECT_ID and SCAN_ID to run the script with these parameters.

```curl
SCAN_ID=""
PROJECT_ID=""
echo "Scan ID is: " $SCAN_ID
echo "Project ID is: " $PROJECT_ID
```



4. Send a request to a certain API end-point, all of them are given in the script, to get and parse the required issue data: 

- Issue id (ID)
- Issue name (NAME)
- Issue details (DETAILS)
- Issue severity (SEVERITY)
- Exposure
- CVSS and CWE
- Remedy suggestions (REMEDY)
- Date and time (TIME) when the issue is found 
- Occurrence frequency (OCCURANCES) - how many times the issue was found in the project.
- Project issues (PROJECTISSUES)

After you get the issue data, put it in an array and remove the double quotes, as shown in the example below. Give each value an index in the array.

```curl
GET_ID=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].id' )
ISSUES_ID_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_ID")
a=(); while read -r line; do a+=("$line"); done <<<"$ISSUES_ID_ARRAY"; declare a;
            
GET_OCCURRENCES=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/projects/'$PROJECT_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].occurrences')
ISSUES_PROJECT_OCCURRENCES=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_OCCURRENCES")
l=(); while read -r line; do l+=("$line"); done <<<"$ISSUES_PROJECT_OCCURRENCES"; declare l;
            
GET_NAME=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].name' )
ISSUES_NAME_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_NAME")
b=(); while read -r line; do b+=("$line"); done <<<"$ISSUES_NAME_ARRAY"; declare b;
            
GET_DETAILS=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].details' )
ISSUES_DETAILS_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_DETAILS")
c=(); while read -r line; do c+=("$line"); done <<<"$ISSUES_DETAILS_ARRAY"; declare c;
            
GET_SEVERITY=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].severity' )
ISSUES_SEVERITY_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_SEVERITY")
d=(); while read -r line; do d+=("$line"); done <<<"$ISSUES_SEVERITY_ARRAY"; declare d;
            
GET_EXPOSURE=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].exposure' )
ISSUES_EXPOSURE_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_EXPOSURE")
f=(); while read -r line; do f+=("$line"); done <<<"$ISSUES_EXPOSURE_ARRAY"; declare f;
            
GET_CVSS=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].cvss' )
ISSUES_CVSS_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_CVSS")
g=(); while read -r line; do g+=("$line"); done <<<"$ISSUES_CVSS_ARRAY"; declare g;

GET_CWE=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].cwe' )
ISSUES_CWE_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_CWE")
h=(); while read -r line; do h+=("$line"); done <<<"$ISSUES_CWE_ARRAY"; declare h;
             
GET_REMEDY=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].remedy' )
ISSUES_REMEDY_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_REMEDY")
r=(); while read -r line; do r+=("$line"); done <<<"$ISSUES_REMEDY_ARRAY"; declare r;
                
GET_TIME=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].time' )
ISSUES_TIME_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_TIME")
s=(); while read -r line; do s+=("$line"); done <<<"$ISSUES_TIME_ARRAY"; declare s;
                
GET_PROJECTISSUES=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/projects/'$PROJECT_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'')
```



5. Print how much issues you found in the scan and in the project. Declare new variables and give them a value of 0 (i and k).

```curl
echo "We found ${#a[*]} vulnerabilities in this scan"
                echo "We found  ${#l[*]} issues in this project and now we will filter them and send just new vulnerabilities to Jira"
                len=${#a[*]}
                i=0
                k=0
```



6. Configure the flow that will look up a detected scan issue among the existing project issues and check its occurrence.  

```curl
while [ $i -lt $len ]; do
                    while [ $k -lt ${#l[*]} ]; do
                        declare -A new=([$k]="$GET_PROJECTISSUES")
                        ISSUES_PROJECT=$(sed -e 's/^"//' -e 's/"$//' <<<${new[$k]} | jq '.['$k'].issueIds')
                        o=(); while read -r line; do o+=("$line"); done <<<"$ISSUES_PROJECT"; declare o;
                        if [[ " ${o[*]} " =~ "${a[$i]}" ]]; then
                            if [[ ${l[$k]} -lt 2 ]]; then
                                echo "____________________________________________________________________________________"
                                echo "We have found this issue " ${b[$i]} ${l[$k]} " times in this part of the website, so we will send it to the Jira."
                                echo "____________________________________________________________________________________"
                                jiraPost=$(curl -X 'POST' 'http://192.168.56.1:8086/rest/api/2/issue/' -u 'testing:testing' --data '{
                                                                                                                      "fields": {
                                                                                                                                "project":
                                                                                                                                        {
                                                                                                                                        "key": "JEN"
                                                                                                                                        },
                                                                                                                                        "summary": "'"${b[$i]}"'",
                                                                                                                                        "description": "DETAILS: '"${c[$i]}"',\\nDISCOVERED: '"${s[$i]}"',\\nSEVERITY: '"${d[$i]}"',\\nEXPOSURE: '"${f[$i]}"',\\nREMEDY: '"${r[$i]}"',\\nCVSS: '"${g[$i]}"',\\nCWE: '"${h[$i]}"'", 
                                                                                                                                        "issuetype": {
                                                                                                                                                     "name": "Task"
                                                                                                                                                     },
                                                                                                                                                     "customfield_10300": "Some Custom Value"
                                                                                                                                                }
                                                                                                                                            }' -H "Content-Type: application/json")
                                echo $jiraPost
                            else
                                echo "We have found this issue " ${b[$i]} ${l[$k]} " times in this part of the website, so we will not send it to Jira"
                            fi
                        fi
                    let k++
                    done
                let i++
                k=0
                done
                 '''
            }
        }
    }
}
```



The first `while` loop here runs until the value of your variable (s) reaches the value of the total issues found in the scan. The variable (i) is incremented each time the `while` loop inside it (the second `while` loop) completes its work. And each time the script returns the value of the variable (k) to 0 to use it in the second `while` loop.

In the second `while` loop,  declare each time a new array in which the project issues are assigned and the value of that array depends on the variable (k), which is incremented by 1 each time to find each issue.

After that, take the issue from the scan and the issues from the array where the project issues are given, and see if the issue from the scan is there. Check the occurrences, that is how many times that issue was found there. 

- If it is found less than 2 times, that is once, send that issue to Jira.
- If it is found more than 2 times, print the following message: "We have found this issue " (Issue name) (How many times you found this issue)" times in this part of the website, so we will not send it to Jira".

The loop stays all active until you check each value.

7. Optional. Send custom fields to Jira.  
   You can also see in the post request how to send a custom field to Jira. It is important that you make that custom field in Jira and enter the correct name of it (you can find the real name of a custom field in the settings of that custom field in Jira, in the URL section).

After the second `while` loop is completed, the issue is changed and the variable (k) is set to 0 to look for the second issue in the project again.

## Example of running the script inside a scan

Below is a sample script that runs a scan from the Jenkins pipeline against a vulnerable benchmark application and sends new issues to Jira. 

```curl
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
           RESULT=$(nexploit-cli scan:polling --interval 30s --timeout 20m --token $BRIGHT_TOKEN --breakpoint high_issue $SCAN_ID)
           if [ -z "$RESULT" ]
           then
               echo "Failed to stop scan"
           else
               echo "Stop Scan 🛑"
               nexploit-cli scan:stop --token $BRIGHT_TOKEN $SCAN_ID
           fi
            sleep 20
            jq --version
            PROJECT_ID=""
            echo "Scan ID is: " $SCAN_ID
            echo "Project ID is: " $PROJECT_ID
            
            GET_ID=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].id' )
            ISSUES_ID_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_ID")
            a=(); while read -r line; do a+=("$line"); done <<<"$ISSUES_ID_ARRAY"; declare a;
            
            GET_OCCURRENCES=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/projects/'$PROJECT_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].occurrences')
            ISSUES_PROJECT_OCCURRENCES=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_OCCURRENCES")
            l=(); while read -r line; do l+=("$line"); done <<<"$ISSUES_PROJECT_OCCURRENCES"; declare l;
            
            GET_NAME=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].name' )
            ISSUES_NAME_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_NAME")
            b=(); while read -r line; do b+=("$line"); done <<<"$ISSUES_NAME_ARRAY"; declare b;
            
            GET_DETAILS=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].details' )
            ISSUES_DETAILS_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_DETAILS")
            c=(); while read -r line; do c+=("$line"); done <<<"$ISSUES_DETAILS_ARRAY"; declare c;
            
            GET_SEVERITY=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].severity' )
            ISSUES_SEVERITY_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_SEVERITY")
            d=(); while read -r line; do d+=("$line"); done <<<"$ISSUES_SEVERITY_ARRAY"; declare d;
            
            GET_EXPOSURE=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].exposure' )
            ISSUES_EXPOSURE_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_EXPOSURE")
            f=(); while read -r line; do f+=("$line"); done <<<"$ISSUES_EXPOSURE_ARRAY"; declare f;
            
            GET_CVSS=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].cvss' )
            ISSUES_CVSS_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_CVSS")
            g=(); while read -r line; do g+=("$line"); done <<<"$ISSUES_CVSS_ARRAY"; declare g;

            GET_CWE=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].cwe' )
            ISSUES_CWE_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_CWE")
            h=(); while read -r line; do h+=("$line"); done <<<"$ISSUES_CWE_ARRAY"; declare h;
                
            GET_REMEDY=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].remedy' )
            ISSUES_REMEDY_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_REMEDY")
            r=(); while read -r line; do r+=("$line"); done <<<"$ISSUES_REMEDY_ARRAY"; declare r;
                
            GET_TIME=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/scans/'$SCAN_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'' | jq '.[].time' )
            ISSUES_TIME_ARRAY=$(sed -e 's/^"//' -e 's/"$//' <<<"$GET_TIME")
            s=(); while read -r line; do s+=("$line"); done <<<"$ISSUES_TIME_ARRAY"; declare s;
                
            GET_PROJECTISSUES=$(curl -s -X 'GET' 'https://app.brightsec.com/api/v1/projects/'$PROJECT_ID'/issues' -H 'accept: application/json' -H 'Authorization: Api-Key '$BRIGHT_TOKEN'')

            echo "We found ${#a[*]} vulnerabilities in this scan"
            echo "We found  ${#l[*]} issues in this project and now we will filter them and send just new vulnerabilities to Jira"
            len=${#a[*]}
                i=0
                k=0
                while [ $i -lt $len ]; do
                    while [ $k -lt ${#l[*]} ]; do
                        declare -A new=([$k]="$GET_PROJECTISSUES")
                        ISSUES_PROJECT=$(sed -e 's/^"//' -e 's/"$//' <<<${new[$k]} | jq '.['$k'].issueIds')
                        o=(); while read -r line; do o+=("$line"); done <<<"$ISSUES_PROJECT"; declare o;
                        if [[ " ${o[*]} " =~ "${a[$i]}" ]]; then
                            if [[ ${l[$k]} -lt 2 ]]; then
                                echo "____________________________________________________________________________________"
                                echo "We have found this issue " ${b[$i]} ${l[$k]} " times so we will send it to the Jira."
                                echo "____________________________________________________________________________________"
                                jiraPost=$(curl -X 'POST' 'http://192.168.56.1:8086/rest/api/2/issue/' -u 'testing:testing' --data '{
                                                                                                                      "fields": {
                                                                                                                                "project":
                                                                                                                                        {
                                                                                                                                        "key": "JEN"
                                                                                                                                        },
                                                                                                                                        "summary": "'"${b[$i]}"'",
                                                                                                                                        "description": "DETAILS: '"${c[$i]}"',\\nDISCOVERED: '"${s[$i]}"',\\nSEVERITY: '"${d[$i]}"',\\nEXPOSURE: '"${f[$i]}"',\\nREMEDY: '"${r[$i]}"',\\nCVSS: '"${g[$i]}"',\\nCWE: '"${h[$i]}"'", 
                                                                                                                                        "issuetype": {
                                                                                                                                                     "name": "Task"
                                                                                                                                                     },
                                                                                                                                                     "customfield_10300": "Some Custom Value"
                                                                                                                                                }
                                                                                                                                            }' -H "Content-Type: application/json")
                                echo $jiraPost
                            else
                                echo "We have found this issue " ${b[$i]} ${l[$k]} " times on this part of website, so we will not send it to Jira"
                            fi
                        fi
                    let k++
                    done
                let i++
                k=0
                done
                 '''
     }
   }
 }
}
```