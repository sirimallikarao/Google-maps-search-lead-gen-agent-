# Google Maps Lead Generation Agent - N8N Workflow
An automated lead generation system that extracts business contact information from Google Maps and enriches the data with AI-generated insights.

# 🚀 Features
Automated Google Maps Scraping: Extracts business listings from Google Maps search results
Intelligent Data Processing: Systematically processes multiple pages of search results
AI-Powered Enrichment: Uses Groq AI to generate likely contact emails and business backgrounds
Google Sheets Integration: Automatically stores and updates data in Google Sheets
Real-time Processing: Triggers on new data additions for continuous enrichment

# 📋 What It Does
Search & Extract: Searches Google Maps for businesses based on your query
Data Collection: Extracts business name, address, phone, website, rating, and hours
AI Enhancement: Generates professional email addresses and business descriptions
Storage: Saves all data to Google Sheets with unique identifiers
Enrichment: Automatically enhances records with additional contact info

# 🛠️ Workflow Components
#Main Workflow

AI Agent: Orchestrates the entire lead generation process
Map Search Tool: Queries Google Maps API via Serper
Google Sheets Tool: Stores extracted business data
Chat Trigger: Allows manual initiation of searches

# Data Enrichment Workflow

Google Sheets Trigger: Monitors for new entries
Groq AI Integration: Generates emails and business backgrounds
Batch Processing: Handles multiple records efficiently

# 📊 Data Structure
Each business record contains:

UUID: Unique identifier for tracking
Name: Business name
Address: Complete business address
Number: Phone number (without + prefix)
Website: Business website URL
Rating: Google Maps rating
Opening Hours: Business operating hours
Email: AI-generated professional email
Background: AI-generated business description

# ⚙️ Setup Requirements
API Keys & Credentials

# Serper API: For Google Maps data extraction

# Get your API key from Serper.dev
Add to X-API-KEY header in Map Search Tool

# OpenAI API: For the main AI agent
Configure in OpenAI Chat Model node
Recommended model: gpt-4o-mini
# Groq API: For data enrichment
Get API key from Groq
Configure in HTTP Request header authentication
# Google Sheets API: For data storage
Set up Google Sheets OAuth2 credentials
Create a new spreadsheet or use existing one

## Google Sheets Setup

Create a new Google Spreadsheet
Add the following columns:

UUID
Name
Address
Number
Website
Rating
Opening Hours
Email
Background
Update the documentId in all Google Sheets nodes with your spreadsheet ID

# 🔧 Configuration
Geographic Settings
The workflow is currently configured for India:

# Coordinates: 17.3749816,78.5173563,17z (Hyderabad area)
Language: English (hl=en)
Country: India (gl=in)

# To change location, update the ll, gl, and location parameters in the Map Search Tool.
Search Parameters
Maximum Pages: 5 pages per search (configurable)
Temperature: 0.1 for consistent AI responses
Batch Processing: Processes items individually for reliability

# 📝 Usage
Starting a Search

Open the chat interface for the workflow
Send a message with your search query, for example:

"Dental Clinic Ahmedabad"
"Restaurants Mumbai"
"Digital Marketing Agency Bangalore"

# Monitoring Progress

The AI agent provides real-time updates: "Processing page X of 5"
Check your Google Sheets for extracted data
Watch as records get enriched with AI-generated emails and backgrounds

# Data Flow
Search Query → Google Maps API → Data Extraction → Google Sheets Storage → AI Enrichment → Updated Records
🔒 Privacy & Compliance

Rate Limiting: Built-in delays prevent API abuse
Data Accuracy: AI-generated emails are estimates based on business info
Compliance: Ensure your use complies with Google's Terms of Service
Data Storage: All data is stored in your private Google Sheets

# 🚨 Important Notes
Email Generation: Generated emails are educated guesses, not verified addresses
API Limits: Monitor your API usage across all services
Data Quality: Results depend on Google Maps data availability
Rate Limits: The workflow includes built-in throttling for API compliance

# 🔄 Workflow Architecture
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│   Chat Trigger  │ → │    AI Agent      │ → │  Google Sheets  │
└─────────────────┘    └──────────────────┘    └─────────────────┘
                              │
                              ↓
                    ┌──────────────────┐
                    │ Map Search Tool  │
                    └──────────────────┘
                              
┌─────────────────────────────────────────────────────────────────┐
│                    Data Enrichment Loop                         │
│                                                                 │
│ Sheets Trigger → Filter → Batch Loop → Groq AI → Update Sheets │
└─────────────────────────────────────────────────────────────────┘
# 📈 Performance Tips

Batch Size: Process one record at a time to avoid API timeouts
Error Handling: Built-in retry logic for failed requests
Data Validation: Filters out header rows and empty records
Memory Management: Uses window memory for conversation context

# 🛡️ Error Handling

JSON Parsing: Robust error handling for malformed AI responses
API Failures: Graceful degradation with "N/A" fallbacks
Rate Limiting: Automatic delays between requests
Data Validation: Filters invalid records before processing

# 📞 Support
If you encounter issues:
Check API key configurations
Verify Google Sheets permissions
Monitor API rate limits
Review n8n execution logs

Dm me for any doubts :www.linkedin.com/in/basaveni-sirimallika-rao-b9b88a323
