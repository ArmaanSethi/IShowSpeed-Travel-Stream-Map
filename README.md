# IShowSpeed Travel Stream Map

[![AI Assisted](https://img.shields.io/badge/AI%20Assisted-Gemini%202.5%20Pro-blueviolet)](https://gemini.google.com)

An interactive world map showcasing the countries IShowSpeed has visited during his IRL (In Real Life) travel streams, complete with details, highlights, and links.

## About This Project

This project aims to be a comprehensive, fan-maintained resource tracking IShowSpeed's global streaming adventures. It provides an easy way to visualize where he's been, when, and some key moments from each trip.

**Origin:** This map was primarily generated through iterative prompting and refinement using Google's **Gemini 2.5 Pro**, leveraging its research capabilities (see `research.md`) to gather travel data and its coding abilities within the collaborative **Canvas** environment to build the interactive webpage. While AI provided the foundation, the data accuracy relies on publicly available information and may require community updates.

## Live Demo

[**➡️ View the Live Map Here ⬅️**](https://i-show-speed-travel-stream-map.vercel.app/)

## Features

* **Interactive World Map:** Built with Leaflet.js for smooth panning and zooming.
* **Clean Base Map:** Uses CartoDB Positron tiles for better data visibility.
* **Country Highlighting:** Visited countries are clearly colored on the map.
* **Current Trip Highlight:** The country for the current ongoing trip (if any) is highlighted in a distinct color (green).
* **Flag Markers:** Uses country flag icons for clear identification of visited locations, especially smaller countries. Markers are placed using manually specified coordinates for better accuracy.
* **Hover Tooltips:** Hovering over a country area or its flag marker shows quick information (Country, Time Ago, Highlights Snippet).
* **Click Popups:** Clicking a country area or its flag marker reveals a detailed popup with:
    * Full highlights description.
    * Relative time since the visit (e.g., "9 months ago").
    * Approximate month and year of the visit.
    * Links to search YouTube for related streams/VODs or direct video links.
* **Smooth Zoom:** Clicking a country/marker smoothly zooms the map to focus on that location.
* **README Modal:** Clicking the "About" button fetches and displays this README file directly within the page.
* **Podcast Player:** Includes an embedded HTML audio player for the associated podcast file.
* **Favicon:** Includes a map-themed favicon for browser tabs.
* **Easy Data Updates:** Travel information is stored in a clearly structured JavaScript array (`travelData`) within `index.html`, making community updates straightforward.

## Technology Stack

* **HTML:** Page structure
* **CSS:** Styling via [Tailwind CSS](https://tailwindcss.com/)
* **JavaScript:** Core logic, interactivity, data handling
* **[Leaflet.js](https://leafletjs.com/):** Interactive map library
* **[Luxon.js](https://moment.github.io/luxon/):** Date/time handling (for "time ago")
* **[marked.js](https://marked.js.org/):** Markdown parser (for rendering README in modal)
* **[flagcdn.com](https://flagcdn.com/):** Source for country flag icons
* **[Natural Earth Data](https://www.naturalearthdata.com/):** GeoJSON country boundaries (via CDN)
* **AI Assistance:** [Google Gemini 2.5 Pro](https://gemini.google.com) & Canvas environment

## Project Structure

The project currently consists of:

* `index.html`: The main file containing all HTML, CSS, JavaScript, and the core `travelData`.
* `README.md`: This file, providing information about the project.
* `research.md`: Contains the detailed research notes (primarily from Gemini) used to compile the initial travel data points for the map.
* `__iShowSpeed's Global Glitch_...__.wav`: The podcast audio file. (Ensure this filename is exact).
* `LICENSE`: (Recommended) Should contain the full text of the chosen license (e.g., MIT).

## How to Update Map Data

Keeping the map accurate relies on community contributions! Updating is designed to be simple:

1.  **Fork & Clone (Recommended):** See the "Contributing" section below for the best way to make changes via GitHub.
2.  **Edit `index.html`:** Open the file in a text editor or code editor.
3.  **Locate `travelData`:** Find the JavaScript array variable named `travelData` near the top of the main `<script>` block. It's clearly marked with comments.
4.  **Modify or Add Trip Objects:**
    * Each trip is represented by an object `{...}` within the `travelData = [...]` array.
    * **To Add:** Copy an existing object `{...}`, add a comma `,` after the preceding object, paste the copied object, and modify its values.
    * **To Modify:** Find the object for the country/trip you want to change and edit its property values.
    * **Properties:**
        * `country`: (String) Country name (e.g., `"Japan"`).
        * `iso_a2`: (String) **Crucial!** The 2-letter ISO 3166-1 alpha-2 country code (e.g., `"JP"`). Must be correct for highlighting and flag display. Find codes [here](https://en.wikipedia.org/wiki/ISO_3166-1_alpha-2).
        * `date`: (String) Approximate date of the *start* or key moment of the visit in `"YYYY-MM-DD"` format (e.g., `"2023-07-25"`).
        * `lat`: (Number) Approximate latitude for the flag marker (e.g., `35.7`). Use tools like [latlong.net](https://www.latlong.net/) to find a good central point for the mainland/key area.
        * `lon`: (Number) Approximate longitude for the flag marker (e.g., `139.7`).
        * `highlights`: (String) Description of key moments/activities. Keep it concise but informative.
        * `links`: (Array of Strings) Related links. Format options:
            * Search link: `"Search YouTube: 'Your Search Query'"`
            * Direct URL: `"https://www.youtube.com/results?search_query=1"`
        * `current`: (Boolean) `true` if this is the *current* ongoing trip, `false` otherwise. **Only one trip should be `true` at a time.** Update the previous `current: true` entry to `false` when adding a new current trip.
5.  **Save and Commit:** Save your changes to `index.html` and commit them (see "Contributing").

## Contributing

Contributions are highly welcome to keep this map accurate and up-to-date! Whether it's adding a missed trip, correcting details, fixing a bug, or improving the design, please feel free to contribute.

The best way to contribute is via the standard GitHub workflow:

1.  **Fork the Repository:** Click the "Fork" button on the top right of the repository page on GitHub. This creates your own copy.
2.  **Clone Your Fork:** Clone your forked repository to your local machine:
    ```bash
    git clone [https://github.com/ArmaanSethi/IShowSpeed-Travel-Stream-Map.git](https://github.com/ArmaanSethi/IShowSpeed-Travel-Stream-Map.git)
    cd ishowspeed-travel-map
    ```
3.  **Create a Branch:** Create a new branch for your changes:
    ```bash
    git checkout -b fix/update-japan-data # Or feature/add-country-x
    ```
4.  **Make Changes:** Edit the `index.html` file (especially the `travelData` array) or other files as needed.
5.  **Commit Changes:** Stage and commit your changes with a clear message:
    ```bash
    git add index.html
    git commit -m "Update: Corrected highlights for Japan trip"
    ```
6.  **Push to Your Fork:** Push your changes to your branch on GitHub:
    ```bash
    git push origin fix/update-japan-data
    ```
7.  **Open a Pull Request:** Go to your forked repository on GitHub. You should see a prompt to create a Pull Request from your new branch to the original repository. Click it, review your changes, add a description, and submit the Pull Request.

**Areas for Contribution:**

* Adding newly completed trips.
* Correcting dates, highlights, or links for existing trips.
* Improving the accuracy of `lat`/`lon` coordinates for markers.
* Fixing any display bugs or improving responsiveness.
* Enhancing the UI/UX (e.g., legend clarity, modal design).
* Improving accessibility.

## Feedback & Suggestions

Have ideas or found a bug? Please **open an issue** on the GitHub repository! Clear descriptions and steps to reproduce (for bugs) are appreciated.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
