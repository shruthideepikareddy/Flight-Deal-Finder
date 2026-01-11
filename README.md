# ✈️ Flight Deal Finder

A powerful Python-based application that automates the search for cheap flights and notifies users when prices drop below their specified thresholds. It integrates multiple APIs to bridge the gap between real-time flight data and personalized user alerts.

## 🚀 Features

- **Automated Price Monitoring**: Regularly checks for the cheapest flights from a base location to multiple destinations.
- **IATA Code Integration**: Automatically retrieves and updates IATA airport codes for destinations using the Amadeus API.
- **Direct & Indirect Search**: Intelligent search logic that first looks for direct flights and falls back to indirect flights (with stopovers) if no direct options are available.
- **Multi-Channel Notifications**:
  - **Email**: Sends detailed flight alerts to a list of users managed via Google Sheets.
  - **WhatsApp/SMS**: Integrates with Twilio to provide instant mobile alerts.
- **Dynamic Data Management**: Uses Sheety to interface with Google Sheets as a database for destination prices and user contact information.

## 🛠️ Technology Stack

- **Python**: Core application logic.
- **Amadeus API**: Real-time flight search and location data.
- **Sheety API**: Integration with Google Sheets for data storage.
- **Twilio API**: SMS and WhatsApp notification delivery.
- **SMTP**: Email notification handling.
- **Dotenv**: Secure environment variable management.

## 📋 Prerequisites

Before running the application, ensure you have:
1. Python 3.x installed.
2. API Keys for:
   - [Amadeus](https://developers.amadeus.com/)
   - [Sheety](https://sheety.co/)
   - [Twilio](https://www.twilio.com/)
3. A Google Sheet set up with two tabs: `prices` (columns: City, IATA Code, Lowest Price) and `users` (columns: First Name, Last Name, Email).

## ⚙️ Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/flight-deal-finder.git
   cd flight-deal-finder
   ```

2. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure Environment Variables**:
   Create a `.env` file in the root directory and add the following:
   ```env
   AMADEUS_API_KEY=your_amadeus_key
   AMADEUS_SECRET=your_amadeus_secret
   SHEETY_USERNAME=your_sheety_username
   SHEETY_PASSWORD=your_sheety_password
   SHEETY_PRICES_ENDPOINT=your_prices_endpoint
   SHEETY_USERS_ENDPOINT=your_users_endpoint
   TWILIO_SID=your_twilio_sid
   TWILIO_AUTH_TOKEN=your_twilio_token
   TWILIO_VIRTUAL_NUMBER=your_twilio_phone
   TWILIO_VERIFIED_NUMBER=your_personal_phone
   TWILIO_WHATSAPP_NUMBER=your_twilio_whatsapp
   MY_EMAIL=your_email
   MY_EMAIL_PASSWORD=your_app_password
   EMAIL_PROVIDER_SMTP_ADDRESS=smtp.gmail.com
   ```

## 🖥️ Usage

Run the main script to start the search:
```bash
python main.py
```

The script will:
1. Fetch destinations from your Google Sheet.
2. Update missing IATA codes.
3. Check for flights within the next 6 months.
4. Notify all users if a price lower than the "Lowest Price" in the sheet is found.
