# 🚀 Demandbase Export API — Postman Collection

A ready-to-use Postman collection for testing and working with the Demandbase Export API.

This collection allows you to:

- Create export jobs across multiple data types
- Monitor job status
- Retrieve exported data
- Explore available fields for each entity
- Retrieve available reference objects and reference object fields

---

## 📦 Get Started

### Option 1 — Download Collection

Grab the collection JSON from this repository and import it into Postman:

1. Download the collection file from this repository
2. Open Postman
3. Click **Import**
4. Upload the JSON file

---

## 🔐 Authentication

All requests use **Bearer Token authentication**.

1. Generate a token via the Demandbase Auth API
2. Set the token in Postman:

```text
bearerToken = YOUR_ACCESS_TOKEN
```

---

## ⚙️ Environment Variables

Set these variables in Postman:

```text
baseURL = https://uapi.demandbase.com
exportAPIPath = data/export/v1
bearerToken =
jobID =
object =
```

---

## 🧩 Collection Structure

### 📊 Fields

#### Get Fields

Retrieve available fields for a given entity type, such as Account.

Example endpoint:

```text
GET {{baseURL}}/{{exportAPIPath}}/fields?entityType=Account
```

---

### 📤 Export Jobs

#### Create Export Job

Create an export job for supported entity types.

Supported entity types include:

- Account
- Opportunity
- Person
- Activity
- Ad Report Data
  - Campaign
  - Creative
- Buying Group Data
  - accountBuyingGroup
  - personBuyingGroupMember

The collection includes a sample export job request using the Activity entity type.

Example endpoint:

```text
POST {{baseURL}}/{{exportAPIPath}}/job
```

Export jobs may include:

- Filters
- Field selection
- Date ranges
- Entity-specific parameters

---

### 📣 Third-Party Campaign Export Jobs

Create campaign summary export jobs for supported third-party ad sources.

Supported sources include:

- LinkedIn
- Google

Example use case:

```text
Create third-party campaign export job (LinkedIn and Google only)
```

---

### 📋 Specialized Jobs

The collection includes specialized export job endpoints for:

- Account list exports
- Person list exports

Example endpoints:

```text
POST {{baseURL}}/{{exportAPIPath}}/accountlist/Job
POST {{baseURL}}/{{exportAPIPath}}/personList/job
```

---

### 📋 Job Management

#### List Jobs

View submitted export jobs.

Example endpoint:

```text
GET {{baseURL}}/{{exportAPIPath}}/jobs
```

#### Get Job Status

Check the status of a specific export job using `jobID`.

Example endpoint:

```text
GET {{baseURL}}/{{exportAPIPath}}/job/{{jobID}}
```

---

### 🧾 Reference Data

#### Get Available Reference Objects

Retrieve available reference objects.

Example endpoint:

```text
GET {{baseURL}}/{{exportAPIPath}}/references
```

#### Get Reference Data Fields for an Object

Retrieve available fields for a specific reference object.

Example endpoint:

```text
GET {{baseURL}}/{{exportAPIPath}}/reference/{{object}}
```

---

## 🔄 Typical Workflow

1. Authenticate
2. Get Fields or Reference Data
3. Create Export Job
4. Check Job Status
5. Download Results

---

## 🧠 Notes & Tips

- Jobs are asynchronous — polling is required
- Use smaller limit values for testing
- Field names follow `{Entity}.fieldName` format
- Filters support operators like `Exists` and `Contains`
- Activity exports require a date range
- Buying Group exports require account-level context, such as account IDs

---

## 🛠 Troubleshooting

### 401 Unauthorized

Check that `bearerToken` is set and valid.

### Empty Results

Validate:

- Entity type
- Field names
- Filters
- Date range
- Account IDs or list IDs, where applicable

### Job Stuck in Progress

Large datasets can take time. Try using a smaller date range, fewer fields, or a lower limit while testing.

---

## 📚 Related Resources

- [Developer Documentation](https://developer.demandbase.com/)
