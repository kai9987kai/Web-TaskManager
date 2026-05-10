# Browser Task Manager Pro

**Browser Task Manager Pro** is an advanced client-side diagnostics dashboard that works like a browser-safe mini task manager. It displays system information, browser/device capabilities, performance estimates, network details, cookies, battery status, memory usage, storage usage, permissions, feature support, and live runtime logs.

The project is built as a single HTML file using standard browser APIs, Chart.js, and Anime.js. It is designed to be easy to run, easy to modify, and useful for debugging browser environments without needing a backend server.

---

## Overview

Browser Task Manager Pro gives users a modern dashboard for inspecting what a web page is allowed to know about the current device and browser.

It includes:

- System specification detection
- CPU/main-thread load estimate
- GPU/WebGL renderer detection
- Memory usage chart
- Public IP lookup
- Cookie manager
- User agent inspection
- Website state monitoring
- Battery information
- Network diagnostics
- Storage quota monitor
- Permission audit
- Display and input details
- Performance timeline
- Browser feature detection
- Live event/debug log
- Dark/light mode
- JSON snapshot export

Because browsers do not expose true operating-system Task Manager data, the CPU and GPU panels use safe browser-side estimates instead of pretending to read real hardware usage directly.

---

## Features

### System Specs

The dashboard detects and displays useful device and browser information, including:

- Platform
- Operating system guess
- Browser guess
- Language and browser languages
- CPU core count
- Device memory hint
- GPU renderer
- GPU vendor
- WebGL/WebGL2 support
- Maximum texture size
- Screen resolution
- Available screen size
- Color depth
- Pixel ratio
- Timezone

---

### CPU / Main Thread Load

The CPU panel provides a browser-safe estimate of current main-thread pressure.

It uses signals such as:

- Event-loop delay
- FPS health
- Long Task API count
- Frame timing

This does **not** read real OS CPU usage. Browsers block that level of access for privacy and security reasons.

---

### GPU / Graphics Signal

The GPU panel estimates graphics pressure using:

- WebGL availability
- WebGL2 availability
- Renderer information
- Frame rate stability
- Pixel ratio
- Main-thread pressure

It also displays the detected WebGL renderer where the browser allows it.

---

### Memory Usage

The memory panel uses browser-supported memory information when available.

Supported information may include:

- Used JavaScript heap
- JavaScript heap limit
- Estimated memory usage percentage
- Device memory fallback hint

Some browsers hide detailed memory values, so the dashboard falls back safely when exact data is not available.

---

### Optional IP Information

The IP panel can fetch public IP information using an external lookup service.

It can show:

- Public IP address
- City
- Region
- Country
- ISP / organization
- Timezone
- ASN

For privacy, the upgraded version does **not** automatically request IP information. The user must click the button to load it.

---

### Cookie Manager

The cookie manager allows users to inspect and manage cookies visible to the current page.

Features include:

- View current cookies
- Set a new cookie
- Choose cookie expiration in days
- Delete individual cookies
- Clear visible cookies
- Refresh cookie list

Cookies are limited by normal browser rules. A page can only access cookies available to its own domain/path and cannot read `HttpOnly` cookies.

---

### User Agent Inspector

The User Agent panel displays:

- Raw user agent string
- Browser guess
- User-Agent Client Hints, where available
- Mobile hint
- Platform hint

This is useful for testing browser detection and compatibility handling.

---

### Website State Monitor

The Website States panel tracks live page status, including:

- Page load time
- Network type
- Online/offline state
- Page visibility
- Focus state
- Current URL
- Referrer
- Page age

It also listens for online, offline, visibility, focus, and resize events.

---

### Battery Information

When supported by the browser, the dashboard shows:

- Battery percentage
- Charging status
- Charging time
- Discharging time

If the Battery Status API is unavailable or blocked, the dashboard displays a safe fallback instead of crashing.

---

### Network Diagnostics

The Network Diagnostics panel includes:

- Online status
- Effective connection type
- Downlink estimate
- RTT estimate
- Save Data mode
- Manual latency sample

The latency test attempts a lightweight request and displays an estimated response time.

---

### Storage Monitor

The Storage Monitor shows available browser storage information, including:

- Estimated quota usage
- Total available quota
- Persistent storage status
- `localStorage` key count
- `sessionStorage` key count
- IndexedDB availability

This is useful for debugging browser storage-heavy apps.

---

### Permission Audit

The Permission Audit checks supported browser permissions, such as:

- Geolocation
- Notifications
- Camera
- Microphone
- Clipboard read
- Clipboard write
- Persistent storage

Unsupported permission checks are handled gracefully.

---

### Display & Input Panel

The Display & Input panel reports:

- Viewport size
- Screen size
- Device pixel ratio
- Screen orientation
- Touch point count
- Pointer type
- Reduced motion preference
- Preferred color scheme
- Contrast preference

This helps when testing responsive layouts and accessibility behavior.

---

### Performance Timeline

The Performance Timeline panel displays browser performance metrics such as:

- Navigation type
- DOM interactive time
- DOMContentLoaded time
- Load complete time
- First Paint
- First Contentful Paint
- Resource count
- Transfer size
- Long task count
- Time origin

---

### Feature Detection

The Feature Detection panel checks support for modern web APIs, including:

- WebGL
- WebGL2
- WebGPU
- Web Workers
- Service Workers
- WebAssembly
- Battery API
- Network Information API
- Clipboard API
- Storage Estimate API
- PerformanceObserver
- Device Memory API

---

### Event Log

The dashboard includes a live event log that records:

- Dashboard startup
- Theme changes
- Refresh events
- Online/offline changes
- Visibility changes
- Resize events
- Cookie actions
- IP lookup events
- Runtime errors
- Promise rejection errors

The log can be cleared at any time.

---

## Screenshots

Add screenshots here when available.

```markdown
![Browser Task Manager Pro Screenshot](assets/screenshot.png)
````

---

## Tech Stack

Browser Task Manager Pro uses:

* **HTML5**
* **CSS3**
* **Vanilla JavaScript**
* **Chart.js**
* **Anime.js**
* **WebGL**
* **Performance APIs**
* **Storage APIs**
* **Permissions API**
* **Battery Status API**
* **Network Information API**

No build system is required.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/browser-task-manager-pro.git
cd browser-task-manager-pro
```

Open the HTML file directly:

```bash
index.html
```

Or serve it locally:

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

---

## Usage

1. Open the page in a modern browser.
2. Click **Task Manager** or **Open Dashboard**.
3. Explore the dashboard cards.
4. Use the search bar to filter cards.
5. Use the category dropdown to focus on system, performance, network, privacy, browser, or developer panels.
6. Use the refresh dropdown to change the update interval.
7. Click **Pause** to stop live updates.
8. Click **JSON** to export a diagnostics snapshot.
9. Click **Copy** to copy the snapshot to your clipboard.

---

## Keyboard Shortcuts

| Shortcut | Action                                       |
| -------- | -------------------------------------------- |
| `Esc`    | Close dashboard                              |
| `T`      | Toggle dark/light mode                       |
| `Space`  | Pause/resume updates while dashboard is open |

---

## Privacy Notes

Browser Task Manager Pro is mostly client-side.

Most panels use local browser APIs only. However, the optional IP lookup contacts an external service when the user clicks **Load IP Information**.

The app does not require a backend server.

The app does not read files from the device.

The app cannot access private operating-system task-manager data.

The app cannot access cookies from other websites.

The app cannot access `HttpOnly` cookies.

The app cannot bypass browser permission controls.

---

## Important Limitations

Web browsers intentionally restrict hardware and system access.

Because of that:

* CPU usage is an estimate, not real OS CPU usage.
* GPU usage is an estimate, not real OS GPU usage.
* RAM is usually a browser/device hint, not exact installed memory.
* Battery data may be unavailable in many browsers.
* Network data may be unavailable or approximate.
* Permissions depend on browser support.
* GPU renderer data may be hidden or reduced by privacy settings.
* Public IP location may be approximate.

This project is designed to be transparent about those limitations.

---

## Browser Support

Best results are expected in modern Chromium-based browsers.

| Browser         | Support                                     |
| --------------- | ------------------------------------------- |
| Chrome          | Strong                                      |
| Edge            | Strong                                      |
| Brave           | Strong, some privacy APIs may be restricted |
| Firefox         | Partial                                     |
| Safari          | Partial                                     |
| Mobile browsers | Partial                                     |

Some APIs are experimental, deprecated, privacy-restricted, or browser-specific.

---

## File Structure

A simple version of the project can be structured like this:

```text
browser-task-manager-pro/
├── index.html
├── README.md
├── assets/
│   └── screenshot.png
└── LICENSE
```

The current version can run as a single standalone `index.html` file.

---

## Main Components

### Dashboard Popup

The dashboard opens as a full-screen modal-style interface with cards, filters, controls, and live telemetry.

### Metrics Cards

Each card focuses on a specific diagnostic area, such as system specs, cookies, network, storage, battery, or performance.

### Charts

Chart.js powers:

* CPU/main-thread estimate chart
* GPU/graphics pressure chart
* Memory usage doughnut chart

### Animations

Anime.js powers entrance animations and small UI transitions.

### Snapshot Export

The dashboard can export a structured JSON diagnostics snapshot.

This is useful for:

* Debugging browser issues
* Sharing environment details
* Testing web compatibility
* Recording runtime state
* Comparing browser behavior

---

## Example Snapshot Data

A snapshot may contain:

```json
{
  "meta": {
    "app": "Browser Task Manager Pro",
    "exportedAt": "2026-05-10T18:30:00.000Z",
    "page": "http://localhost:8000/",
    "note": "Hardware readings are browser API hints or safe estimates."
  },
  "system": {
    "Operating System": "Windows",
    "CPU Cores": "8",
    "RAM Hint": "8 GB"
  },
  "performance": {
    "estimatedMainThreadLoadPercent": 22,
    "estimatedGraphicsPressurePercent": 18,
    "fps": 60,
    "longTasks": 0
  }
}
```

---

## Customization

You can customize the dashboard by editing the CSS variables in `:root`.

Example:

```css
:root {
  --primary: #2563eb;
  --primary-2: #7c3aed;
  --success: #16a34a;
  --warning: #f59e0b;
  --danger: #ef4444;
}
```

You can also add new dashboard cards by creating another `.card` inside the dashboard grid:

```html
<article class="card" data-category="developer" data-title="custom diagnostic panel">
  <div class="card-header">
    <div>
      <h3>Custom Panel</h3>
      <p class="card-subtitle">Your custom browser diagnostic feature.</p>
    </div>
    <span class="badge">Custom</span>
  </div>
  <div id="customPanel"></div>
</article>
```

---

## Possible Future Improvements

Planned or possible upgrades:

* PWA support
* Offline dashboard mode
* Export to CSV
* Export to Markdown report
* More detailed resource waterfall
* Better visual FPS meter
* WebGPU diagnostics panel
* WebRTC local network diagnostics
* Service Worker cache inspection
* IndexedDB explorer
* LocalStorage/sessionStorage editor
* Lighthouse-style browser health score
* Plugin-style custom cards
* Multi-tab comparison mode
* Historical snapshot comparison
* Accessibility audit panel
* Security headers checker
* CSP analyzer
* Console log capture overlay

---

## Security Considerations

This project should not be treated as a security scanner.

It is a browser diagnostics tool. It can help inspect exposed browser state, but it cannot verify full system security.

When adding new features, avoid:

* Collecting unnecessary personal data
* Automatically sending diagnostics to a server
* Reading sensitive form fields
* Storing exported snapshots without user consent
* Logging private tokens or credentials
* Making hidden third-party requests

---

## Development Tips

When working on the project:

1. Test in multiple browsers.
2. Check the console for unsupported API warnings.
3. Use local hosting instead of opening the file directly if fetch or storage APIs behave differently.
4. Keep all optional external requests opt-in.
5. Clearly label estimated values.
6. Avoid pretending the browser can access real OS-level CPU/GPU usage.
7. Keep fallback behavior friendly and visible.

---

## Why This Project Exists

Modern browsers expose many useful APIs for understanding performance, capabilities, storage, display, permissions, and runtime state. However, these APIs are scattered and inconsistent across browsers.

Browser Task Manager Pro brings them together into one visual dashboard.

It is useful for:

* Web developers
* Debugging browser compatibility
* Testing device capabilities
* Inspecting runtime performance
* Teaching browser API limitations
* Demonstrating privacy-safe diagnostics
* Building advanced browser tooling experiments

---

## Disclaimer

This dashboard does not access real operating-system task-manager data.

Values such as CPU and GPU usage are estimates based on browser-observable signals. They are intended for debugging and experimentation, not professional hardware monitoring.

For exact hardware monitoring, use operating-system tools such as:

* Windows Task Manager
* macOS Activity Monitor
* Linux System Monitor
* Browser DevTools Performance panel

---

## License

Add your preferred license.

Example:

```text
MIT License
```

---

## Author

Created by **kai9987kai**.

---

## Project Status

Browser Task Manager Pro is an experimental but functional browser diagnostics dashboard. It is suitable for learning, testing, debugging, and further extension.

Contributions, improvements, and new diagnostic cards are welcome.

```
```
