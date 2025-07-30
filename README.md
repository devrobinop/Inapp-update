# In-App Update(Admin)

# Screenshots 
![94125](https://github.com/user-attachments/assets/4c183342-a564-4e1c-861c-ac2340762fcb)



A complete, professional, and modern in-app update system for Sketchware projects. This system allows you to remotely control updates for your user app using a dedicated admin panel app, all powered by the free and reliable GitHub API.

This repository contains the configuration file (`update.json`) that the user app reads. The admin panel app modifies this file directly.

---

![90506](https://github.com/user-attachments/assets/8c0cc129-65ef-4531-a414-7dca0856aeaa)
## 🚀 How to Use This System

Follow these steps to integrate this update system into your own projects.

### Part 1: Setting Up the Backend (GitHub Repository)

This is a one-time setup for your backend.

1.  **Fork this Repository:** Click the "Fork" button at the top-right of this page to create your own copy.
2.  **Get Your Repository Details:**
    *   **Username:** Your GitHub username (e.g., `devrobinop`).
    *   **Repository Name:** The name of your forked repository (e.g., `inapp-update`).
3.  **Get the Permanent Raw Link (for User App):**
    *   In your forked repository, open the `update.json` file.
    *   Click the **"Raw"** button.
    *   Copy the URL from your browser's address bar. This is your permanent link that will **never change**.
    *   **Example Link:** `https://raw.githubusercontent.com/YourUsername/YourRepoName/main/update.json`
4.  **Create a Personal Access Token (Password for Admin App):**
    *   Go to your GitHub **Settings**.
    *   Navigate to **Developer settings** > **Personal access tokens** > **Tokens (classic)**.
    *   Click **"Generate new token"** and choose **"Generate new token (classic)"**.
    *   **Note:** Give it a descriptive name like "Admin Panel Token".
    *   **Expiration:** Set to "No expiration" for convenience.
    *   **Select scopes:** Tick the **`repo`** checkbox. This is crucial as it allows the token to modify files in your repository.
    *   Click **"Generate token"**.
    *   **IMPORTANT:** Copy the generated token (`ghp_...`) immediately and save it in a secure place. You will **not** be able to see it again.

![90506](https://github.com/user-attachments/assets/8c0cc129-65ef-4531-a414-7dca0856aeaa)

### Part 2: Configuring the User App (The App Your Users Install)

1.  **Download the User App `.swb` file.** https://web.sketchub.in/p/31023
2.  Open the project in Sketchware.
3.  Navigate to `MainActivity` -> `initializeLogic` event.
4.  Find the `network.startRequestNetwork` block or ASD code.
5.  Replace the placeholder URL with your **Permanent Raw Link** from Part 1, Step 3.
6.  That's it! Compile the app and distribute it to your users.

![90506](https://github.com/user-attachments/assets/8c0cc129-65ef-4531-a414-7dca0856aeaa)

### Part 3: Configuring the Admin Panel App

1.  **Download the Admin App `.swb` file.** https://web.sketchub.in/p/31023
2.  Open the project in Sketchware.
3.  Navigate to `MainActivity` -> `release_update_button` `onClick` event.
4.  Open the **Add Source Directly (ASD)** block inside this event.
5.  Update these three final String variables at the top of the code:
    ```java
    final String GITHUB_USERNAME = "YourGitHubUsername";
    final String REPO_NAME = "YourRepositoryName";
    final String GITHUB_TOKEN = "Your_ghp_..._Token";
    ```
6.  Compile the admin app and install it on your device.

![90506](https://github.com/user-attachments/assets/8c0cc129-65ef-4531-a414-7dca0856aeaa)

### Part 4: Releasing an Update

1.  Open the **Admin Panel** app on your phone.
2.  Fill in all the fields:
    *   **Version Code:** Must be a number greater than the current version in the user app.
    *   **Version Name:** The display name for the new version (e.g., `1.7.1`).
    *   **Dialog Title:** The title of the update dialog.
    *   **Update APK Link:** The direct download link for your new APK.
    *   **What's New:** Use `\n` for new lines in the changelog.
    *   **Mandatory Update:** Switch this ON if you want to force users to update.
3.  Click **"Release Update"**.
4.  You will see a "Releasing update..." toast, followed by a "Update Released Successfully!" toast.
5.  Done! The next time any user opens your main app, they will see the new update dialog.

---

## ⚠️ Important Notes

**It will take 1-2mins to show update in userapp because GitHub raw link takes time to update**

*   **Token Security:** Never share your Personal Access Token publicly. Treat it like a password.

*   **Libraries:**
*    The admin app requires the `Volley` library.

![90506](https://github.com/user-attachments/assets/8c0cc129-65ef-4531-a414-7dca0856aeaa)
