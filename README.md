How to Setup & Run this Project:

❖ Install NodeJs ( Ignore If Already Installed)
1. Visit the official Node.js website i.e)
https://nodejs.org/en/download/
2. Download the Node.js installer
3. Run the installer.
4. Follow the prompts in the installer.
   
—First Run Backend then Frontend & Admin—

❖ Steps To Setup Backend Of The Project
1. Open Project Folder In VS Code
2. Open Integrated Terminal
3. Type “npm install” and press Enter and Wait for
Installation to be completed (requires Internet)
4. Setup The MongoDB
a. Open cloud.mongodb.com
b. After that Sign Up on the website.
c. Click on New Project Option
d. After Creating Project go to Database Section &
Build a database
e. Select M0 & Your Region & Create Database
f. Setup Username & Password & Create User
Note: Do not use ‘@’ symbol in the password
g. Now Click on Finish & Close
h. In security tab, click on network access section and click on "Add IP Address" button. Whitelist IP 0.0.0.0 & Click on Add Entry
i. Now Click on Connect
j. Now Select Compass Option under developer tools section.
k. And Copy the Connection String
l. And Paste It in db.js within the brackets of "await mongoose.connect(" ")". replace <password> with your account password
you set previously & save changes
5. Now We have to Set Up stripe
● Open .env file in backend folder paste your stripe secret
key in STRIPE_SECRET_KEY variable
6. To Run Backend use npm run server in Integrated Terminal


❖ Steps To Run Frontend & Admin Panel Of The Project
1. Open Project Folder In VS Code
2. Open Integrated Terminal in project directory
○ Right Click on Sidebar > Select “Open In Integrated
Terminal”
3. Type “npm install” and press Enter and Wait for
Installation to be completed (requires Internet)
4. After Installation You will See ‘node_modules’ Folder in
the Sidebar
5. After that type “npm run dev” in terminal
6. Now Your Project Will Start In Your Default Web Browser
7. Do the above 6 steps for both frontend and admin sections. 

## Deployment Guide

### Prerequisites
- Make sure you have a [GitHub](https://github.com) account.
- Ensure your project is already hosted on GitHub.

### Step 1: Setup Your Backend
1. **Edit `server.js` for Deployment:**
    - Open your `server.js` file and modify the port configuration:
      ```javascript
      const port = process.env.PORT || 4000;
      ```

2. **Push Your Project to GitHub:**
    - Initialize a Git repository if you haven't already:
      ```sh
      git init
      git add .
      git commit -m "Initial commit"
      git branch -M main
      git remote add origin <YOUR_GITHUB_REPO_URL>
      git push -u origin main
      ```
    - If it's an existing repository, just push the latest changes:
      ```sh
      git add .
      git commit -m "Deploy preparation"
      git push
      ```

### Step 2: Deploy the Backend on Render
1. **Create a New Web Service:**
    - Go to [Render.com](https://render.com) and log in.
    - Click on "New" and select "Web Service".
    - Choose "Connect a GitHub repo" and authenticate if prompted.
    - Select your repository (e.g., `food-delivery`) and click "Connect".

2. **Configure the Service:**
    - Set the name to `foodel-backend`.
    - Set the root directory to `backend`.
    - Set the runtime environment to `Node`.
    - Set the build command to:
      ```sh
      npm install
      ```
    - Set the start command to:
      ```sh
      node server.js
      ```
    - Add the environment variables:
      - Click on "Environment" and add variables from your `.env` file.

3. **Deploy the Service:**
    - Click on "Create Web Service" and wait for the deployment to complete.
    - Copy the URL of the deployed backend.

### Step 3: Update Frontend and Admin with Backend URL
1. **Update URLs in Your Project:**
    - Replace the local backend URLs in your frontend and admin code with the deployed backend URL.
    - For example, in your frontend context file (`context/StoreContext.js`):
      ```javascript
      const backendUrl = 'https://your-backend-url.onrender.com';
      ```

2. **Push the Updated Code:**
    - Commit and push these changes to GitHub:
      ```sh
      git add .
      git commit -m "Update backend URL"
      git push
      ```

### Step 4: Deploy the Frontend on Render
1. **Create a New Static Site:**
    - Go back to Render.com and click on "New" -> "Static Site".
    - Select your repository and authenticate if prompted.
    - Set the name to `foodel-frontend`.
    - Set the root directory to `frontend`.
    - Set the build command to:
      ```sh
      npm install && npm run build
      ```
    - Set the publish directory to `frontend/build`.

2. **Deploy the Site:**
    - Click on "Create Static Site" and wait for the deployment to complete.
    - Copy the URL of the deployed frontend.

### Step 5: Deploy the Admin Panel on Render
1. **Create a New Static Site for Admin:**
    - Repeat the steps as for the frontend, but this time use the `admin` directory.
    - Set the name to `foodel-admin`.
    - Set the root directory to `admin`.
    - Set the build command to:
      ```sh
      npm install && npm run build
      ```
    - Set the publish directory to `admin/build`.

2. **Deploy the Site:**
    - Click on "Create Static Site" and wait for the deployment to complete.
    - Copy the URL of the deployed admin panel.

### Step 6: Configure Routing (for React Router)
1. **Add Rewrites for SPA:**
    - In Render.com, go to your frontend and admin service settings.
    - Add the following rewrite rule under "Redirects/Rewrites":
      ```plaintext
      Source:    /*
      Destination: /index.html
      ```

### Conclusion
Your project should now be successfully deployed with the backend, frontend, and admin panel all accessible via their respective URLs.
