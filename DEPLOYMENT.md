# Deploying to Cloudflare Pages (NOT Workers)

**IMPORTANT:** This project must be deployed as a **Cloudflare Page**, not a generic Worker.

## 1. Delete Incorrect Project (Optional)
If you created a "Worker" project that asks for a "Deploy command" in the build settings, it is likely the wrong project type. Consider deleting it to avoid confusion or simply create a new one.

## 2. Create the Correct Project
1.  Log in to the [Cloudflare Dashboard](https://dash.cloudflare.com/).
2.  Go to **Workers & Pages**.
3.  Click **Create application**.
4.  **CLICK THE "PAGES" TAB** (This is the critical step! Do not stay on the "Workers" tab).
5.  Click **Connect to Git**.
6.  Select your repository (`bhr`).

## 3. Configure Build Settings
*   **Project Name**: `bhr-website` (or similar).
*   **Production Branch**: `master`.
*   **Framework Preset**: `None`.
*   **Build Command**: `npm run pages:build`
*   **Build Output Directory**: `.vercel/output/static`

## 4. Save and Deploy
Click **Save and Deploy**. Cloudflare handles the rest automatically.

## Troubleshooting
*   **"Workers-specific command in a Pages project"**: You are using the wrong project type (Worker instead of Pages) or have extraneous settings in `wrangler.toml`.
*   **"Peer dependency" errors**: resolved by the `.npmrc` file included in the repository.
