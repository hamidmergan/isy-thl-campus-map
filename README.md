# ISY THL Campus Map

An interactive campus map application for Technische Hochschule Lübeck (THL) featuring animated visualizations, interactive quizzes, and gamification elements.

## Features

- **Interactive Campus Map**: Animated Lottie-based campus map with smooth zoom and pan controls
- **Building Information**: Detailed information for each building including opening hours and descriptions
- **Interactive Quizzes**: H5P-integrated quiz system with 10 campus-related questions
- **Gamification System**: 
  - Badge system with 3 unlockable achievements
  - Progress tracking with localStorage persistence
  - Visual notifications for earned badges
- **Customizable Filters**: 
  - Toggle visibility of map elements (quiz markers, bike stations, bus stops, cafés, buttons)
  - "Toggle All" feature for quick show/hide of all filters
  - Filter preferences saved to localStorage
- **Responsive Design**: Optimized for desktop, tablet, and mobile devices
- **Additional Features**:
  - Coffee shop locations
  - Bicycle repair station markers
  - Bus stop information with route details
  - Quick access buttons (FabLab, cafeteria menu, campus tour, etc.)

## Tech Stack

- **Frontend**: Pure HTML, CSS, JavaScript (no framework dependencies)
- **Animation**: Lottie-web for interactive SVG animations
- **UI Framework**: Bootstrap 5.3.2 for responsive components
- **Icons**: Font Awesome 5.15.4
- **Quiz Integration**: H5P (external)

## Project Structure

```
isy-thl-campus-map/
├── index.html           # Main HTML file
├── css/
│   └── style.css       # Application styles
├── js/
│   ├── config.js       # Configuration data (buildings, quizzes, badges)
│   └── main.js         # Application logic and event handlers
├── assets/
│   ├── campus_map_intro.json  # Lottie animation data
│   ├── campus_map.svg          # Static campus map SVG
│   ├── badges/                 # Badge SVG assets
│   └── [building images]       # Building photos and icons
└── README.md
```

## Installation & Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/isy-thl-campus-map.git
   cd isy-thl-campus-map
   ```

2. **Serve the application** (required due to CORS restrictions):
   ```bash
   npx serve
   ```
   Or use any other local server:
   ```bash
   python -m http.server 3000
   # or
   php -S localhost:3000
   ```

3. **Open in browser**:
   Navigate to `http://localhost:3000`

## Usage

### Navigation
- **Pan**: Click and drag on the map
- **Zoom**: Use mouse wheel or pinch gestures (mobile)
- **Skip Intro**: Press any key or tap the screen during the intro animation

### Interacting with Elements
- **Buildings**: Click on any building to view detailed information
- **Quiz Markers**: Click on question marks to start a quiz
- **Buttons**: Access quick links to various campus resources
- **Coffee Shops**: View café locations and opening hours
- **Bike Stations**: Find bicycle repair stations
- **Bus Stops**: Check bus routes and schedules

### Settings
- Access settings via the gear icon in the top-right corner
- Toggle individual map element categories
- Use "Toggle All" to show/hide all elements at once
- Reset progress to clear quiz completions and badges

### Badges
- View earned badges via the medal icon in the top-right corner
- Badges are earned by completing quizzes:
  - **Stay Curious**: Complete your first quiz
  - **Challenge Accepted**: Complete 5 quizzes
  - **Campus Expert**: Complete all 10 quizzes

## Development

### Key Files

- **`js/config.js`**: Contains all configuration data including:
  - Quiz modal definitions
  - Building information
  - Filter configurations
  - Badge definitions

- **`js/main.js`**: Application logic including:
  - Lottie animation initialization
  - Filter system
  - Event handlers for map interactions
  - H5P quiz integration
  - Badge system

- **`css/style.css`**: All styling including:
  - Responsive design rules
  - Animation definitions
  - Component styles

### Local Storage

The application uses localStorage to persist:
- Quiz completion status (`h5p_completed_ids`)
- Quiz results (`h5p_quiz_results`)
- Filter preferences (`filter_settings`)

### Customization

To customize the map:
1. Update building data in `js/config.js`
2. Add/modify images in the `assets/` folder
3. Adjust Lottie animation in `assets/campus_map_intro.json`
4. Modify quiz questions via H5P (external integration)

## Important Notes

### H5P Quizzes

The application uses H5P quizzes embedded via iframes. **Note that the quiz iframes will show 404 errors without proper CORS access** to the H5P server endpoint (`/wp-admin/admin-ajax.php`).

**Options:**
- **Replace with your own quizzes**: Update the `quizModals` configuration in `js/config.js` with your own H5P content IDs and server URLs
- **Hide quiz markers**: If you don't have H5P integration, simply toggle off the "Quiz" option in the settings menu to hide all quiz markers from the map
- **Remove quiz functionality**: Delete or comment out the quiz-related elements in `js/config.js` if not needed

The map works fully without quizzes - the quiz system is optional and can be disabled through the filter settings.
