# 🚀 Demandbase Export API — Postman Collection

A ready-to-use Postman collection for testing and working with the Demandbase Export API.

This collection allows you to:
- Authenticate with Demandbase APIs
- Create export jobs across multiple data types
- Monitor job status
- Retrieve exported data
- Explore available fields for each entity

---

## 📦 Get Started

### Option 1 — Download Collection
Grab the collection JSON and import into Postman:

1. Download the collection file from this repository  
2. Open Postman  
3. Click **Import**  
4. Upload the JSON file  

---

## 🔐 Authentication

All requests use **Bearer Token authentication**.

1. Generate a token via the Demandbase Auth API  
2. Set the token in Postman:

bearerToken = YOUR_ACCESS_TOKEN

---

## ⚙️ Environment Variables

Set these variables in Postman:

baseURL = https://uapi.demandbase.com  
exportAPIPath = data/export/v1  
bearerToken = <your token>  
jobID = <used for job status checks>  

---

## 🧩 Collection Structure

### 📊 Fields
- Get Fields  
  Retrieve available fields for a given entity type (e.g., Account)

---

### 📤 Export Jobs

#### Create Export Job
Supports multiple entity types:
- Account
- Opportunity
- Person
- Activity
- Ad Report Data
  - Campaign
  - Creative
- Buying Group Data
  - accountBuyingGroup
  - personBuyingGroup  

Includes:
- Filters
- Field selection
- Date ranges

#### Specialized Jobs
- Third-party campaign exports (LinkedIn, Google)
- Account list exports
- Person list exports

---

### 📋 Job Management

- List Jobs — View submitted export jobs  
- Get Job Status — Check status using jobID  

---

## 🔄 Typical Workflow

1. Authenticate  
2. Get Fields (optional)  
3. Create Export Job  
4. Check Job Status  
5. Download Results  

---

## 🧠 Notes & Tips

- Jobs are asynchronous — polling is required  
- Use smaller limit values for testing  
- Field names follow {Entity}.fieldName format  
- Filters support operators like Exists and Contains  

---

## 🛠 Troubleshooting

**401 Unauthorized**
- Check bearerToken  

**Empty results**
- Validate filters and date range  

**Job stuck in progress**
- Large datasets can take time—try smaller queries first  

---

## 📚 Related Resources

- [Developer Documentation](https://developer.demandbase.com/docs/export-overview)
