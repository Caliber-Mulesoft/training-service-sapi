# training-service-sapi
#PROJECT NAME
  Trainer Reports sapi

# ABOUT THE PROJECT
  The Trainer Reports system API is designed to expose Caliber as an endpoint. 
  It accepts information from a process API and returns relevant data in a JSON format. 
  The information returned should include information about a trainer and their batches.
  For more information, see Usage Examples.

# BUILT WITH
  Anypoint Platform:
    Anypoint Studio
    Anypoint Design Center
    Anypoint Exchange
  
# GETTING STARTED
  Please refer to the SETUP document for more detailed installation steps.

# PREREQUISITES
  URLs in the config.yaml file (src/main/resources/config.yaml) must be updated to
  production URLs. As they are, they point to mock services.

# ENVIRONMENT VARIABLES
  <!-- If there are any environment variables or special code
       snippets that are required for the API to run properly,
       paste them here and label what they are. For example 
       
       password: t|-|iS1SaP@S$W0rD
     -->

# USAGE EXAMPLES
  
## /training
  Get batchIds - Gets all batchIDs. Must be filtered by trainer email.
  
  example query parameter (required): mock1022.employee870e1a69-f385-4cdb-9c59-986de917eca4@mock.com

  example output (JSON):
    [
      {
        "batchId": "TR-1028"
      },
      {
        "batchId": "TR-1004"
      },
      {
        "batchId": "TR-1032"
      },
      {
        "batchId": "TR-1003"
      }
    ]

## /{trainerEmail}
  Get Trainer Info - Gets trainer email, first name, and last name by email.

  example query parameter (required): mock1022.employee870e1a69-f385-4cdb-9c59-986de917eca4@mock.com

  example output (JSON):
  {
    "email": "mock1022.employee870e1a69-f385-4cdb-9c59-986de917eca4@mock.com",
    "firstName": "Mock 1022",
    "lastName": "Employee 1022"
  }

## /batch
  Get Batches (Training Version) - Gets all batches in the training format.
  Must be filtered by batch ID for a specific batch.
  For more info, look at the batchTrainingDataType.raml in the DataTypes folder. 

  example query parameter (required): TR-1028

  example output (JSON):
    [
      {
        "id": 16,
        "batchId": "TR-1028",
        "name": "Mock Batch 16",
        "startDate": "2020-04-01",
        "endDate": "2020-06-10",
        "skill": "Java React",
        "location": "Reston",
        "type": "Corporate",
        "goodGrade": 70,
        "passingGrade": 80,
        "employeeAssignments": {
          "role": "ROLE_LEAD_TRAINER",
          "employee": {
            "email": "mock1022.employee870e1a69-f385-4cdb-9c59-986de917eca4@mock.com",
            "firstName": "Mock 1022",
            "lastName": "Employee 1022"
          },
          "deletedAt": null
        }
      },
      {
        "associateAssignments": [
          {
            "trainingStatus": "Training",
            "associate": {
              "email": "mock0.associate59e1088a-6e5d-4cb7-9d36-9463a2beb2bc@mock.com",
              "salesforceId": "SF-1250",
              "firstName": "Mock 0",
              "lastName": "Associate 0",
              "flag": null
            },
            "startDate": "2020-06-10",
            "endDate": "2020-04-01",
            "active": true
          },
          {
            "trainingStatus": "Training",
            "associate": {
              "email": "mock10.associate6d293e73-1aec-48a5-a0ed-ed8829c9e7f3@mock.com",
              "salesforceId": "SF-1260",
              "firstName": "Mock 10",
              "lastName": "Associate 10",
              "flag": null
            },
            "startDate": "2020-06-10",
            "endDate": "2020-04-01",
            "active": true
          }
        ],
        "currentWeek": 11
      }
    ]

## /current
  Get Current Batches - Gets all current batches from Caliber.

  example output (JSON):
    [
      {
        "id": 16,
        "batchId": "TR-1028",
        "name": "Mock Batch 16",
        "startDate": "2020-04-01",
        "endDate": "2020-06-10",
        "skill": "Java React",
        "location": "Reston",
        "type": "Corporate",
        "goodGrade": 70,
        "passingGrade": 80,
        "employeeAssignments": {
          "role": "ROLE_LEAD_TRAINER",
          "employee": {
            "email": "mock1022.employee870e1a69-f385-4cdb-9c59-986de917eca4@mock.com",
            "firstName": "Mock 1022",
            "lastName": "Employee 1022"
          },
          "deletedAt": null
        }
      },
      {
        "associateAssignments": [
          {
            "trainingStatus": "Training",
            "associate": {
              "email": "mock0.associate59e1088a-6e5d-4cb7-9d36-9463a2beb2bc@mock.com",
              "salesforceId": "SF-1250",
              "firstName": "Mock 0",
              "lastName": "Associate 0",
              "flag": null
            },
            "startDate": "2020-06-10",
            "endDate": "2020-04-01",
            "active": true
          },
          {
            "trainingStatus": "Training",
            "associate": {
              "email": "mock10.associate6d293e73-1aec-48a5-a0ed-ed8829c9e7f3@mock.com",
              "salesforceId": "SF-1260",
              "firstName": "Mock 10",
              "lastName": "Associate 10",
              "flag": null
            },
            "startDate": "2020-06-10",
            "endDate": "2020-04-01",
            "active": true
          }
        ],
        "currentWeek": 11
      }
    ]

## /trainers
  Get All Trainers - Gets all trainers.

  example output (JSON):
    {
      "firstName": "Mock 1027",
      "lastName": "Employee 1027",
      "email": "mock1027.employee74df14df-5842-4811-a57c-be9836537a40@mock.com",
      "trainingBatches": [
        {
          "role": "ROLE_LEAD_TRAINER",
          "employee": {
            "email": "mock1027.employee74df14df-5842-4811-a57c-be9836537a40@mock.com",
            "firstName": "Mock 1027",
            "lastname": "Employee 1027"
          },
          "deletedAt": null
        },
        {
          "role": "ROLE_LEAD_TRAINER",
          "employee": {
            "email": "mock1027.employee74df14df-5842-4811-a57c-be9836537a40@mock.com",
            "firstName": "Mock 1027",
            "lastname": "Employee 1027"
          },
          "deletedAt": null
        }
      ],
      "tier": "ROLE_LEAD_TRAINER"
    }

## /batches
  Get Batches (Qc Version) - Gets all batches in the QC version.
  For more info, look at the batchQCDataType.raml in the DataTypes folder.

  example query parameter (required): TR-1028

  example output (JSON):
    [
      {
        "BatchId": "TR-1201",
        "StartDate": "2021-02-22",
        "EndDate": "2021-05-15"
      },
      {
        "BatchId": "TR-1201",
        "StartDate": "2021-01-01",
        "EndDate": "2021-03-15"
      }
    ]

# ROADMAP
  <!--Include a list of bugs/issues and possible future fixes here. 
      Don't fill this out until we reach code freeze or if you are ready to deploy.-->

# ADDITIONAL MATERIAL
  N/A

# AUTHORS
  Josh Cushing
  Carlos Quimson
  Divyesh Patel
  Keyur Patel
