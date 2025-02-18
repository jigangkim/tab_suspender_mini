# Tab suspender extension

This extension improves browser performance by automatically suspending inactive tabs, reducing memory and CPU usage. It offers flexibility with customizable settings and user-defined exceptions. Based on [Tab Suspender Mini extension for Firefox](https://addons.mozilla.org/en-US/firefox/addon/tab-suspender-mini/).

## Installation

```bash
git clone https://github.com/jigangkim/tab_suspender_mini
cd tab_suspender_mini
zip -r my-extension.xpi manifest.json src/* icons/*
```

Manually install extension via .xpi file under [about:debugging#/runtime/this-firefox](about:debugging#/runtime/this-firefox). Regular version of firefox only allows temporary installation of unsigned extensions. Use the developer version to permanently install the extension.

## Features

### Tab Suspension
- **Automatic Suspension:** Inactive tabs are automatically suspended after a user-defined delay (default: 1 minute). Suspended tabs are replaced with a custom suspension page that stores the original URL and title.
- ~~**Screenshot Capture:** Captures a screenshot of the tab before suspension (where supported).~~
- **Manual Suspension:** Users can manually suspend tabs at any time for increased control.
- **(Added) Manual Bulk Suspension:** Users can manually suspend all tabs except current tab.
- **(Added) Manual Bulk Unsuspension:** Users can manually unsuspend all suspended tabs.
- **(Added) Remove Duplicate Tabs:** Users can manually remove all duplicate tabs including suspended tabs.

### Exception Handling
- **Domain Exceptions:** Maintain a list of domains that will not be suspended. The extension checks URLs against this list before suspending tabs.

### Special Cases
- **Audio Playback Protection:** Tabs playing audio will not be suspended to avoid interruptions.
- **Browser-Specific URLs:** Ignores certain internal browser URLs (e.g., `about:`, `chrome:`, `moz-extension:`) to ensure smooth operation.

### Under the Hood Optimization
- **(Added) Discard Before Redirecting to the Suspended Page:** Call native Firefox discard API and then redirect to the suspended page to free memory.