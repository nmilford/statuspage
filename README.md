# Statuspage
> Self hosted status page written in golang!

This is a small status page project with Postgres as the backing datastore.
There should be no need to change the go code to customize the page.
We use environment variables for configuration, this also includes the logo.

![Dashboard](screenshot.png?raw=true "Dashboard")

## Configuration

We use environment variables to configure the service. The table bellow contains
all variables you can use.

|Name             |Description|
|-----------------|-----------|
|API_TOKEN        |This is the token clients should use to access the API (AUTHORIZATION header)|
|POSTGRES_ADDRESS |The address of the postgres instance|
|POSTGRES_USER    |The postgres username for authorization|
|POSTGRES_PASSWORD|The postgres password for authorization|
|POSTGRES_DB      |The postgres db name|
|SITE_OWNER       |The owner of the side, visible in page title|
|SITE_COLOR       |The background color applied on the header element|
|SITE_LOGO        |Custom logo, served from another site or local path inside the static folder|


## API request examples

Create new service
```bash
curl -H "Authorization: 123" -v -d '{"Group":"External API","Enabled": true, "Name": "User API", "Status": "Operational", "Description": "User API for customers"}' -H "Content-Type: application/json" -X POST http://localhost/api/services
```

Create new incident
```bash
curl -H "Authorization: 123" -v -d '{"time": "2018-01-01T13:50:00-08:00", "status":"Identified", "message":"oh no! i am broken", "Title":"User API is down"}' -H "Content-Type: application/json" -X POST http://localhost/api/incidents
```
