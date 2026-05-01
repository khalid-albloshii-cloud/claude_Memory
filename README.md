# Claude Memory Bank: Automation & Workflows

## 👤 User Context
- **Name:** Khalifa
- **Role:** Head of Mining Section, MOEI
- **Primary Focus:** AI-driven automation workflows (n8n, Python, Claude) for data extraction, travel booking, and market monitoring.

## 🛠️ Technical Preferences
- **Languages & Tools:** Python 3.x, n8n, Playwright, SQLite.
- **Coding Style:** Modular Python scripts (avoid single giant files). Always use robust error handling for scraping operations.
- **Market Analysis:** Preference for tracking technical indicators (RSI, support/resistance) on tech and AI infrastructure stocks.

## 🚗 Active Project Protocol: Emirates Auction Monitor
This section dictates how Claude must handle new auction monitoring tasks.

**The Workflow Trigger:**
Whenever I share this repository link to start a new coding session for an auction, Claude MUST execute the following sequence:

1. **Ask for the Target:** Claude must immediately ask: *"Which auction endpoint or link are we targeting today?"* Do not assume the previous URL.
2. **Analyze the API:** Once the new link is provided, write a script to sniff the API and confirm the structure and `AuctionTypeId`.
3. **Apply the Standard Monitoring Logic:**
   - **Main Poll:** Scan the endpoint every 20 seconds.
   - **Live Info Poll:** Scan live updates (if applicable, like `AuctionBidderInfo`) every 8 seconds.
4. **The "Disappearing Item" Rule (Crucial):** The script must maintain a live map of all active items. If an item is present in one scan but missing in the next, it MUST be logged as **SOLD** using its last known price and total bids.
5. **Data Persistence:** 
   - Save full history to a local SQLite `.db` file.
   - Append sold items to a `.csv` log named dynamically based on the current auction category (e.g., `plates-dubai_data.csv`).
