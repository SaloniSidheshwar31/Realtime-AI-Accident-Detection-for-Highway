# Automated Road Accident Detection and Emergency Response System

## Overview
The **Automated Road Accident Detection and Emergency Response System** is a novel project designed to detect road accidents in real-time using YOLO (You Only Look Once) object detection and other advanced AI techniques. Upon detecting an accident, the system:

1. **Sends Emergency Alerts**: Utilizes the Twilio API to send notifications and make calls to nearby hospitals.
2. **Integrates Current Location**: Includes the accident's geographical location to guide emergency responders accurately.
3. **Minimizes Response Time**: Ensures timely medical assistance by prioritizing hospitals based on proximity.

## Features
- **Real-Time Accident Detection**: Implements YOLO for precise and quick detection of road accidents.
- **Twilio API Integration**: Sends emergency alerts through SMS and calls.
- **Location Integration**: Captures and sends the exact location of the accident using GPS.
- **Scalable Backend**: Processes accident data and manages communications efficiently.
- **User-Friendly Dashboard**: Visualizes data and system operations for easier monitoring.

## Prerequisites
- Python 3.8 or higher
- Libraries: `yolov5`, `opencv-python`, `pandas`, `numpy`, `flask`, `requests`
- Twilio Account with API credentials
- Google Maps API for geolocation services

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/road-accident-detection.git
   cd road-accident-detection
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Configure environment variables:
   - Create a `.env` file in the project root directory.
   - Add the following details:
     ```env
     TWILIO_ACCOUNT_SID=your_account_sid
     TWILIO_AUTH_TOKEN=your_auth_token
     TWILIO_PHONE_NUMBER=your_twilio_phone_number
     GOOGLE_MAPS_API_KEY=your_google_maps_api_key
     ```

4. Start the application:
   ```bash
   python app.py
   ```

## Twilio API Integration
The Twilio API facilitates sending emergency notifications via SMS and phone calls. The process includes:

1. **Setting Up Twilio**:
   - Sign up for a [Twilio account](https://www.twilio.com/).
   - Obtain your Account SID, Auth Token, and a verified phone number.

2. **Sending Alerts**:
   - When an accident is detected, the system generates an alert that includes:
     - A short message describing the incident.
     - The accident's exact location as a Google Maps link.

   Example code snippet for sending alerts:
   ```python
   from twilio.rest import Client

   def send_emergency_alert(location):
       client = Client(TWILIO_ACCOUNT_SID, TWILIO_AUTH_TOKEN)

       message = client.messages.create(
           body=f"Accident detected at {location}. Immediate assistance required!",
           from_=TWILIO_PHONE_NUMBER,
           to="recipient_phone_number"
       )

       print(f"Alert sent: {message.sid}")
   ```

## Location Integration
- The system captures the current location of the accident using GPS.
- The Google Maps API generates a shareable link for responders to access the exact location.

Example code snippet for fetching location:
```python
import requests

def get_location():
    response = requests.get('https://www.googleapis.com/geolocation/v1/geolocate?key=GOOGLE_MAPS_API_KEY')
    location_data = response.json()
    lat = location_data['location']['lat']
    lng = location_data['location']['lng']
    return f"https://maps.google.com/?q={lat},{lng}"
```

## Usage
1. Run the application and ensure all APIs and detection models are configured.
2. Monitor the dashboard for real-time accident detection.
3. Emergency alerts will be triggered automatically when an accident is detected.

## Project Structure
- `models/`: Pre-trained YOLO model files
- `scripts/`: Detection and alert scripts
- `app.py`: Main application file
- `templates/`: Frontend dashboard templates
- `static/`: Static files (CSS, JS)

## Contributions
Contributions are welcome! Feel free to fork the repository and create a pull request with your improvements.

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

## Contact
For queries or feedback, reach out to:
- **Email**: p39salonisidheshwar@gmail.com
- **GitHub**: [SaloniSidheshwar31](https://github.com/SaloniSidheshwar31)

