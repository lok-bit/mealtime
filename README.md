# 🍽️ Mealtime - Random Restaurant Selector

> An interactive restaurant selection tool combining Google Maps API with a spinning wheel feature

![Restaurant Categories](images/curry1.png)
![Wheel Animation](images/winwheel1.png)

## 📖 About

**Mealtime** is a web application designed to solve the common "what should we eat?" dilemma. By integrating Google Maps Places API, users can search for nearby restaurants, filter by categories, and use a spinning wheel feature to make the final decision.

This project was born from a real-life problem: spending too much time discussing where to eat with friends. I developed this tool to make the decision-making process more fun and efficient by combining map search with random selection.

## ✨ Key Features

### 🔍 Restaurant Search
- **Real-time Search**: Google Places Autocomplete provides instant search suggestions
- **Category Filters**: Pre-defined categories including Chinese, Japanese, Hot Pot, Curry, Fast Food, and BBQ
- **Nearby Search**: Searches restaurants within 1km of user's location

### 🗺️ Map Features
- **Interactive Map**: Displays user location and search results
- **Restaurant Info**: Click markers to view name, address, phone number, and rating
- **Route Navigation**: Shows walking route and estimated time from current location

### 🎰 Spin Wheel
- **Visual Wheel**: Smooth wheel animation powered by Winwheel.js
- **Random Selection**: Fair randomization algorithm
- **Auto Navigation**: Automatically displays selected restaurant location and route on map

### 💾 Data Management
- **Local Storage**: Persistent storage using localStorage
- **List Management**: Add, delete, and batch import restaurants
- **Real-time Sync**: Wheel and list updates synchronize automatically

## 🛠️ Tech Stack

### Core Technologies
- **HTML5 / CSS3**: Responsive web design
- **JavaScript (ES6+)**: Vanilla JavaScript implementation
- **Bootstrap 5.3.3**: UI framework and components

### APIs & Libraries
- **Google Maps JavaScript API**: Map and location services
  - Maps API
  - Places API (2024 version)
  - Directions API
- **Winwheel.js**: Wheel animation
- **GSAP (GreenSock)**: Animation engine

## ⚠️ Important Notice

### Current Project Status

**This project uses Google Maps Places API (2024 version)**

> ⚡ Note: Due to Google's gradual deprecation of the old Places API between 2024-2025, **the category search feature is currently not functioning**. This reflects a common real-world development challenge: third-party API updates affecting existing functionality.

### ✅ Working Features
- Search bar restaurant search (using Autocomplete)
- Map display and user location
- Spinning wheel functionality
- Route navigation and walking time calculation
- Restaurant list management (add, delete, local storage)

### ⚠️ Features Requiring Fix
- Right-side category button search (requires upgrade to new Places API's `searchByText`)

### Technical Debt Explanation

This situation demonstrates real challenges in software development:
1. **Third-party Dependency Management**: API version updates affecting existing features
2. **Backward Compatibility Issues**: Old `nearbySearch` marked as deprecated
3. **Upgrade Planning**: Requires refactoring to adapt to new API architecture

To upgrade to the latest API, the following changes are needed:
- Migrate `google.maps.places.PlacesService.nearbySearch` to `google.maps.places.Place.searchByText`
- Migrate `google.maps.Marker` to `google.maps.marker.AdvancedMarkerElement`
- Migrate `google.maps.places.Autocomplete` to `google.maps.places.PlaceAutocompleteElement`
- Add `mapId` parameter to support new Advanced Markers

For detailed migration guide, refer to: [Google Maps Platform Migration Guide](https://developers.google.com/maps/documentation/javascript/places-migration-overview)

## 🚀 Getting Started

### Prerequisites

1. **Google Maps API Key**
   - Visit [Google Cloud Console](https://console.cloud.google.com/)
   - Create a project and enable the following APIs:
     - Maps JavaScript API
     - Places API
     - Directions API
   - Create an API Key

2. **Web Server**
   - Use Live Server or any HTTP server for local development
   - Direct `file://` protocol is not supported

### Installation

1. **Clone Repository**
   ```bash
   git clone https://github.com/yourusername/mealtime.git
   cd mealtime
   ```

2. **Configure API Key**
   
   Find the following code in `index.html` and replace with your API Key:
   ```html
   <script 
       async
       src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY_HERE&loading=async&libraries=places&callback=initMap&region=TW&language=zh-TW">
   </script>
   ```

3. **Start Server**
   ```bash
   # Using Python
   python -m http.server 8000
   
   # Or using Node.js http-server
   npx http-server
   
   # Or using VS Code Live Server
   # Right-click index.html > Open with Live Server
   ```

4. **Open Browser**
   ```
   http://localhost:8000
   ```

## 📁 Project Structure

```
mealtime/
├── index.html          # Main HTML file
├── Winwheel.js        # Wheel animation library
├── README.md          # Project documentation
└── images/            # Project screenshots
```

## 💡 Usage

### Basic Workflow

1. **Allow Location Access**: Grant browser permission to access your location on first use
2. **Search Restaurants**:
   - Use search bar to enter restaurant name
   - Or click category buttons on the right to search by type
3. **Build List**:
   - Click "Add to List" to add individual restaurant
   - Click "Add All" to import all search results
4. **Start Spinning**:
   - Click "Spin" button to start the wheel
   - After wheel stops, restaurant info and route are displayed automatically

### Advanced Features

- **Delete Restaurant**: Click the ✕ button on the right side of restaurant list
- **View Route**: Map automatically displays walking route after selection
- **Persistent List**: Restaurant list is saved automatically for future use

## 🎨 Interface Design

- **Left Panel**: Interactive Google Map
- **Right Panel**: Search interface and restaurant list
- **Side Buttons**: Quick category filters (vertical text orientation)
- **Wheel Animation**: Full-screen overlay for immersive experience

## 🔒 Browser Support

- ✅ Chrome 90+
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

Requires support for:
- Geolocation API
- LocalStorage API
- Canvas API

## 🐛 Known Issues

1. **Category Search Not Working**: Due to using deprecated `nearbySearch` API, right-side category buttons currently not functioning (see "Project Status" above)
2. **API Deprecation Warnings**: Console displays Google Maps API deprecation warnings - this is expected behavior
3. **Location Permission**: Defaults to Taiwan center if user denies location access
4. **Offline Usage**: Requires internet connection to load map and search restaurants

## 🚧 Future Plans

Due to Google Places API version updates, current priority is upgrading to the new API to restore category search functionality.

## 📝 Development Log

### Version History

- **v1.0.0** (2024)
  - Initial release
  - Integrated Google Maps Places API
  - Implemented spinning wheel feature
  - Local storage for restaurant list

## 👨‍💻 About

This project demonstrates my web development skills, including Google Maps API integration, vanilla JavaScript DOM manipulation, data persistence, and third-party library integration. The development process also involved dealing with API version updates, which deepened my understanding of software maintenance and technical debt management.

---

## References

- [Google API Introduction](https://mile.cloud/zh/resources/blog/What-is-Google-API-one-time-to-know-five-types-of-Google-API_60) - What is Google API?
- [Winwheel.js](https://dougtesting.net/winwheel/history) - Wheel animation library
