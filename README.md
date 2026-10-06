# Campus Navigator
# acropolis-navigator

A lightweight, offline-friendly campus wayfinding app for helping new students find labs, departments, offices, classrooms and facilities on a large campus.

## Problem statement

New students can lose time and feel unsure when navigating a large campus, especially when they do not know where a lab, department, office, classroom or everyday facility is located. Campus Navigator provides a searchable campus directory and shows a shortest walking route with simple turn-by-turn directions.

## Features

- Natural-language place search in English and Hinglish, including queries such as “mujhe CS lab jana hai”, “khana kahan milega” and “books”.
- Search matches place names, categories, descriptions and editable keyword tags, with keyboard-accessible autocomplete.
- Category filters show only groups represented in the current campus data.
- Location detail cards show available descriptions, floors and optional service, facilities, hours, contact, accessibility and maintenance fields. Missing information is identified rather than invented.
- Interactive SVG campus map built from places, junctions and weighted roads.
- “I am here” and “I want to go” selectors, route swapping, route clearing, campus-fit and fullscreen controls.
- Shortest walking path calculated with Dijkstra’s algorithm, with an animated route, start/end markers, total distance and approximate walking time.
- Step-by-step walking directions, with live GPS position, nearby mapped places, off-route updates and arrival status when location access is enabled.
- Saved places and recent destinations stored locally in the browser; recent history stores place IDs, not typed search text.
- A persistent light/dark theme toggle and responsive, keyboard-operable map controls.
- Optional voice search using the browser Web Speech API. The microphone button is hidden when speech recognition is unavailable.
- Reduced-motion support and status messages for unavailable browser storage and geolocation errors.
- Pure HTML, CSS and vanilla JavaScript. No packages, network connection or build step are required.

## Data limitations

The bundled AITR map coordinates and walking paths are illustrative estimates, not a surveyed campus map. Confirm them before relying on route guidance. The current dataset does not provide verified emergency contacts, opening hours, wheelchair-accessible paths, maintenance notices, event listings, or additional amenities such as ATMs and washrooms. These are not shown as confirmed campus facts. Add verified details to the optional fields in `CAMPUS_DATA` before presenting them to users.

## Screenshots

Add screenshots of the app here:

- `![Campus Navigator desktop screenshot](screenshots/desktop.png)`
- `![Campus Navigator mobile screenshot](screenshots/mobile.png)`

## How to run

1. Download or clone this repository.
2. Open `index.html` directly in a modern browser (double-click the file).
3. Search for a place or choose a start and destination, then select **Show route**.

The app works locally without a server or internet connection. Voice search is browser-dependent and may require microphone permission or a secure context; all other features work without it.

## How to edit campus data

Open `index.html` and find the clearly marked `CAMPUS DATA` object near the top of the script. It contains the campus places, junctions, roads and shortcuts:

- `places`: each place has a unique `id`, visible `name`, category, description (`detail`), graph `node` id, latitude/longitude and searchable `keywords`. Optional fields include `floor`, `services`, `facilities`, `openingHours`, `contact`, `accessibility` and `status`.
- `junctions`: road intersections have a unique `id`, a short name used in directions and latitude/longitude.
- `roads`: each road connects two place or junction ids. Optional `bends` contain intermediate `[lat, lng]` points; road length is estimated from these coordinates. Roads are treated as two-way.

To add a destination, add its map node to `places`, then connect that id to the walking network with one or more roads. To add an intersection, add it to `junctions` and connect it with roads. Make sure ids are unique and all road endpoints exist. Add English and Hinglish synonyms to `keywords` to improve natural-language search. Add only confirmed information to optional fields.

The SVG map projects latitude/longitude coordinates into its `900 × 640` viewBox. Verify coordinates and walking paths against the real campus before deployment.

## Tech used

- HTML5
- CSS (responsive layout, system-preference dark mode, reduced-motion support)
- Vanilla JavaScript (search ranking, SVG rendering and Dijkstra’s shortest-path algorithm)
- Web Speech API (optional browser voice input)

## Contributing

Contributions are welcome, especially beginner-friendly improvements for Hacktoberfest!

1. Fork the repository and create a focused branch.
2. Make a small, clear change and test it by opening `index.html` in a browser.
3. Keep the app framework-free and offline-friendly.
4. Update the campus data or this README when your change affects them.
5. Open a pull request with a description, testing notes, and screenshots for visual changes.

Please be respectful and welcoming. For a first contribution, look for an issue marked **good first issue** or pick one of these starter tasks:

- Add a new campus place, junction, and connected road.
- Add useful English/Hinglish search keywords to an existing place.
- Improve small-screen spacing or map label readability.
- Add a category icon or a clearer no-results message.
- Test keyboard navigation and report accessibility improvements.
- Add a screenshot to the README.

## Five ideas for future improvements

1. Import a real campus floor plan or map image and calibrate routes to it.
2. Add accessible routes that avoid stairs and steep paths.
3. Support building floors, room numbers and indoor directions.
4. Let campus staff update places and road closures through an importable data file.
5. Add multilingual voice output, estimated wheelchair travel time and live event notices.


