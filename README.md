# Discord Developer Portal Midnight Theme Guide ⭐

Welcome to the **Midnight Theme Guide** for the [Discord Developer Portal](https://discord.com/developers/applications)! This guide will help you enable and explore the **Midnight Theme**, designed for enhanced visibility in low-light environments.

---

## 🌙 Enabling the Midnight Theme

### Method 1: Quick Toggle

1. Open the **[Discord Developer Portal](https://discord.com/developers/applications)**.
2. Rapidly switch between Light and Dark themes **10 times within 3 seconds**.
3. The Midnight theme should activate automatically, giving you a richer, high-contrast experience!

### Method 2: Using Developer Tools (Local Storage)

If you prefer a quick setup through developer tools:

1. Open your browser's **Developer Tools** (usually by pressing `F12` or `Ctrl+Shift+I`).
2. Go to the **Application** tab (or **Storage** in Firefox).
3. In **Local Storage**, locate the key named `devtheme`.
4. Set its value to `"midnight"`.
5. Refresh the page, and enjoy the Midnight theme!
---
 To **exit Midnight mode**, just click the toggle once more to return to Light or Dark mode.
 
---
## 🌌 Midnight Theme Highlights

- **Enhanced Contrast**: Boosted visibility for text and UI elements.
- **Darker Background**: A deeper, comfortable background for low-light use.
- **Persistent Setting**: Your theme preference will be saved and applied each time you open the Developer Portal.

---

## 💻 Sample Code: How the Theme Toggle Works

Here’s a simple example of the code that manages the theme toggling logic:

```javascript
// Define the theme toggle function
function toggleTheme() {
    const timestamp = Date.now();
    toggleTimes.push(timestamp);

    // Check if toggled rapidly within the last 3 seconds
    const rapidToggle = toggleTimes.filter(t => timestamp - t < 3000).length > 10;

    // Limit stored timestamps to last 10 toggles
    while (toggleTimes.length > 10) {
        toggleTimes.shift();
    }

    // Determine the new theme based on rapid toggle
    const newTheme = rapidToggle ? "midnight" : currentTheme === "light" ? "dark" : "light";
    localStorage.setItem("devtheme", newTheme);

    // Apply the new theme
    document.documentElement.classList.toggle("theme-dark", newTheme === "dark");
    document.documentElement.classList.toggle("theme-light", newTheme === "light");
    document.documentElement.classList.toggle("theme-midnight", newTheme === "midnight");

    // Update the current theme
    currentTheme = newTheme;
}

// Initial theme setup
let toggleTimes = [];
let currentTheme = localStorage.getItem("devtheme") || "light";
document.documentElement.classList.add(`theme-${currentTheme}`);
```
---
If you found this guide helpful, please consider leaving a ⭐ on our GitHub repository! Your support helps us improve and create more resources.

Happy developing! 🚀
