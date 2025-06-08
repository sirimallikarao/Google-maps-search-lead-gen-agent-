# 🗺️ Google Maps Lead Generation Agent – n8n Workflow

An automated lead generation system that scrapes business listings from **Google Maps**, enhances data using **AI**, and stores it in **Google Sheets** — perfect for marketers, sales teams, and automation enthusiasts.

---

## 🚀 Features

- 🔍 **Automated Google Maps Scraping**: Extracts business listings from Google Maps using Serper API  
- 🧠 **AI-Powered Enrichment**: Generates likely professional email addresses & business descriptions using Groq AI  
- 🗂️ **Structured Data Storage**: Automatically saves data into Google Sheets with unique tracking  
- 🔁 **Real-time Processing**: Continuously enriches new entries as they are added  
- 📃 **Multi-Page Processing**: Crawls up to 5 pages per search for comprehensive coverage  

---

## 📋 What It Does

1. **Search & Extract**  
   Searches Google Maps for businesses based on user queries.

2. **Data Collection**  
   Gathers business name, address, phone number, website, ratings, and opening hours.

3. **AI Enrichment**  
   Generates likely business emails and a brief background using AI.

4. **Storage**  
   Saves the entire dataset into Google Sheets.

5. **Continuous Enhancement**  
   New entries are automatically enhanced with AI insights.

---

## 🛠️ Workflow Components

### 🔁 Main Workflow

- **AI Agent** – Orchestrates the overall process  
- **Map Search Tool** – Uses Serper API to query Google Maps  
- **Google Sheets Tool** – Handles data writing  
- **Chat Trigger** – Allows manual search initiation

### 🧠 Data Enrichment Workflow

- **Google Sheets Trigger** – Watches for new additions  
- **Groq AI Node** – Enhances records with email & business background  
- **Batch Processor** – Processes multiple records sequentially

---

## 📊 Data Structure

Each business record contains:

| Field           | Description                           |
|----------------|---------------------------------------|
| `UUID`          | Unique ID for tracking               |
| `Name`          | Business name                        |
| `Address`       | Full address                         |
| `Number`        | Phone number (no + prefix)           |
| `Website`       | Website URL                          |
| `Rating`        | Google Maps star rating              |
| `Opening Hours` | Business hours                       |
| `Email`         | AI-generated professional email      |
| `Background`    | AI-generated business description    |

---

## ⚙️ Setup Requirements

### 🔑 API Keys & Configuration

| Service     | Purpose                      | Setup                                     |
|-------------|------------------------------|-------------------------------------------|
| **Serper API** | Google Maps Search            | Get key from [Serper.dev](https://serper.dev), add to `X-API-KEY` in headers |
| **OpenAI API** | Orchestrating search process | Use `gpt-4o-mini`, configure in OpenAI node |
| **Groq API**   | Email & description generation | Add Groq key to HTTP request auth headers |
| **Google Sheets API** | Data storage | Set up OAuth2 credentials, provide spreadsheet ID |

---

## 📝 Google Sheets Setup

1. Create a new Google Spreadsheet  
2. Add the following columns (exact spelling required):

UUID | Name | Address | Number | Website | Rating | Opening Hours | Email | Background

yaml
Copy
Edit

3. Copy the spreadsheet ID and update it in all relevant Google Sheets nodes in n8n

---

## 🌍 Configuration

- **Geographic Defaults**  
  - Location: Hyderabad, India  
  - Coordinates: `17.3749816,78.5173563,17z`  
  - Language: `en`  
  - Country: `in`  

- **To change location**: Update `ll`, `gl`, and `hl` in Map Search Tool parameters

- **Search Parameters**
  - Max Pages: 5  
  - Temperature: 0.1 (for consistent AI responses)  
  - Batch Size: 1 item per iteration (ensures reliability)

---

## ▶️ Usage Guide

### 🔍 Starting a Search

Use the **chat trigger** with a query such as:

Dental Clinic Ahmedabad
Restaurants Mumbai
Digital Marketing Agency Bangalore

yaml
Copy
Edit

### 📊 Monitoring Progress

- Workflow prints updates like: `Processing page X of 5`
- Google Sheet auto-populates with new business entries
- Watch as AI fills in email & business descriptions

---

## 🔁 Data Flow Diagram

Search Query
↓
Google Maps API → Data Extraction → Google Sheets
↓
AI Enrichment (Groq)
↓
Updated Records in Sheets

yaml
Copy
Edit

---

## 🛡️ Error Handling & Reliability

- ✅ **Rate Limiting** – Automatic delays to avoid API blocking  
- ⚠️ **Fallbacks** – Uses `"N/A"` if AI returns an invalid response  
- 🧪 **Validation** – Filters out invalid or incomplete rows before processing  
- ♻️ **Retries** – Handles API failures gracefully

---

## 📈 Performance Tips

- Process one record at a time for optimal API reliability  
- Monitor API rate limits regularly  
- Enable logs in n8n for debugging and error tracing  
- Filter header rows before processing to avoid false triggers  

---

## 🔒 Privacy & Compliance

- ⚠️ AI-generated emails are **educated guesses** — not verified  
- 📜 Ensure compliance with **Google Maps TOS**  
- 🔐 All data stays within **your private Google Sheets**  
- 🧩 Built-in throttling for safer scraping

---

## 🙋‍♀️ Support

For help, feel free to **DM me**:  
🔗 [LinkedIn – Basaveni Sirimallika Rao](https://www.linkedin.com/in/basaveni-sirimallika-rao-b9b88a323)

---

> 💡 Built with ❤️ using n8n, Groq, OpenAI & Google Sheets  
