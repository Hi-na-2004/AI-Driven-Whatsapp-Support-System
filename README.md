**🧠 Adidas Customer Support WhatsApp Bot (n8n + AI)**

An AI-powered WhatsApp customer support assistant built using n8n, Twilio, and a LLM (via Groq).
This bot automates customer interactions for Adidas, handling FAQs, order tracking, and support ticket creation in real time.

**🚀 Features**

💬 WhatsApp Automation via Twilio
🤖 AI Assistant (Alex) for natural conversations
📦 Order Tracking via Airtable
🛍️ Product Queries (inventory lookup)
🎫 Support Ticket Creation
📚 Knowledge Base Integration (Return Policy, etc.)
⏱️ 24/7 automated responses

**🏗️ Architecture Overview**

User (WhatsApp)
   ↓
Twilio Trigger (Webhook)
   ↓
n8n Workflow
   ├── Set Node (Return Policy)
   ├── AI Agent (LangChain + Groq LLM)
   │     ├── order_tracking (Airtable)
   │     ├── order_records (Inventory)
   │     └── create_tickets (Support System)
   ↓
Twilio Response (WhatsApp Message)


**⚙️ Tech Stack**

n8n – Workflow automation
Twilio API – WhatsApp messaging
Groq LLM (openai/gpt-oss-120b) – AI responses
Airtable – Database (Orders, Inventory, Tickets)
LangChain Agent Node – Tool orchestration


**📂 Workflow Components**

1. 📩 Twilio Trigger
Listens for incoming WhatsApp messages
Event: com.twilio.messaging.inbound-message.received

2. 🧾 Return Policy Node

Injects static knowledge:

{
  "return policy": "Return Policy is 5 days"
}

3. 🤖 AI Agent

Handles all conversation logic.

**Capabilities**

FAQ handling (via knowledge base)
Order tracking (asks for order ID)
Product queries (via inventory)
Ticket escalation
Personality
Friendly, human-like assistant named Alex
Concise and professional
Never exposes internal tools


**4. 🛠️ Tools**

📦 order_tracking
Airtable: Orders table
Filters by order_id
Returns delivery status
🛍️ order_records
Airtable: Inventory table
Filters by product_price
🎫 create_tickets
Airtable: Tickets table

Fields:

Name
Notes
Assignee (default: Hassan Mahmood)
Status = Todo

**5. 📤 Twilio Send Message Node**

Sends AI-generated response back to the user via WhatsApp.

**🔄 Conversation Flow**

**✅ General Questions**

Uses knowledge base
Example: return policy, shipping time

**📦 Order Tracking**

Ask for Order ID
Query Airtable
Return:
Delivery status
Expected arrival

**🧑‍💼 Speak to Human**

Ask for:
Name
Issue
Create ticket
Confirm submission

**🧪 Example Interaction**

User: Where is my order?
Bot: Could you please share your order ID?
User: 12345
Bot: Your order is out for delivery and will arrive by tomorrow.

**🔐 Environment Setup**

1. Twilio
Configure WhatsApp Sandbox or Business API
Add webhook → n8n endpoint
2. Airtable

Create 3 tables:

Orders
Inventory
Tickets
3. n8n Credentials
Twilio API
Airtable Token
Groq API
▶️ How to Run
Import workflow JSON into n8n
Configure credentials:
Twilio
Airtable
Groq
Activate workflow
Connect Twilio webhook → n8n URL
Send WhatsApp message → Done ✅

**⚠️ Limitations**

No authentication for users
Relies on Airtable structure
Limited knowledge base (expandable)
No multilingual support (yet)

**🧠 Future Improvements**

Add RAG-based knowledge base
Multi-language support
Analytics dashboard
Order history context
Memory-based conversations

**📌 Notes**

Business operates in EST timezone (AI respects context)
AI avoids hallucination and escalates when unsure
Clean plain-text responses only (WhatsApp-friendly)

**👨‍💻 Author**

Built as an AI-powered automation system using n8n + LLM orchestration.
