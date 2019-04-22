# Sample GraphQL queries

This page contains some set of Request and Response queries examples for ApiChecker API.
If you not sure how to use GraphQL queries, please take a look on Get Started section.


## Get Current User Details

Get email and name for current user (token owner) and information about subscription.
 
Query: 
```graphql
query {
  me {
    email,
    name,
    subscription {
      status,
      plan
    }
  }
}
```

Response:
```json
{
  "data": {
    "me": {
      "email": "test@test.com",
      "name": "Alex Lobanov",
      "subscription": {
        "status": "active",
        "plan": "basic"
      }
    }
  }
}
```


## Get All Monitors
Get all monitors and their monitor URL and current status (+ SSL status)
```graphql
query {
  monitors {
    monitorUrl,
    currentStatus,
    sslInformation {
      valid 
    }
  }
}
```

Response:
```json
{
  "data": {
    "monitors": [
      {
        "monitorUrl": "https://apichecker.com/",
        "currentStatus": "UP",
        "sslInformation": {
          "valid": true
        }
      },
      {
        "monitorUrl": "https://app.apichecker.com/",
        "currentStatus": "UP",
        "sslInformation": {
          "valid": true
        }
      }
    ]
  }
}
```


## Get List of Apps
Get all applications and their monitors with below data:
* Application Name
* List of monitors 
    * Monitoring URL
    * Is Auth Required?
    * Check internal
    * Uptime information for last 24h
    * Current Status
    * Is SSL valid?
    * Last check timing
    
Query: 
```graphql
query {
  apps {
    appName,
  	monitors {
      monitorUrl
      authRequired,
      checkInterval,
      uptime {
        avgHealthLastDay,
      },
      currentStatus,
      sslInformation {
        valid
      }
      lastCheck {
        elapsedTime
      }
    }
  }
}
```

Response:
```json
{
  "data": {
    "apps": [
      {
        "appName": "ApiChecker",
        "monitors": [
          {
            "monitorUrl": "https://apichecker.com/",
            "authRequired": false,
            "checkInterval": 180,
            "uptime": {
              "avgHealthLastDay": 100
            },
            "currentStatus": "UP",
            "sslInformation": {
              "valid": true
            },
            "lastCheck": {
              "elapsedTime": 680
            }
          },
          {
            "monitorUrl": "https://app.apichecker.com/",
            "authRequired": false,
            "checkInterval": 180,
            "uptime": {
              "avgHealthLastDay": 100
            },
            "currentStatus": "UP",
            "sslInformation": {
              "valid": true
            },
            "lastCheck": {
              "elapsedTime": 380
            }
          }
        ]
      }
    ]
  }
}
```

## Pause monitoring

In case if you want to stop one monitor in application:
```graphql
mutation {
    changeMonitorStatus(monitorId: "{yourMonitorID}", enable: true, delay:20000)
}
```

In case if you want to stop whole application monitoring, including all nested monitors:
```graphql
mutation {
  changeApplicationStatus(applicationId: "{yourAppId}", enable: false, delay: 1000)
}
```

As return object you will get `Boolean` value: 
* `true` in case of successfully completed method
* 'false' in case if something went wrong
