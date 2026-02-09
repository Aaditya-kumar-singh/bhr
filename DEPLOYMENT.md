# Deploying to Cloudflare Pages

This project is configured to use `@cloudflare/next-on-pages` for deployment on Cloudflare Pages.

## Prerequisites

1.  A GitHub account with this repository.
2.  A Cloudflare account.

## Step-by-Step Guide

1.  **Log in to Cloudflare Dashboard**: Go to [dash.cloudflare.com](https://dash.cloudflare.com) and log in.
2.  **Navigate to Pages**: Click on "Workers & Pages" in the sidebar, then "Create Application" -> "Pages" -> "Connect to Git".
3.  **Select Repository**: Choose your GitHub account and select the `bhr` repository.
4.  **Configure Build Settings**:
    *   **Project Name**: Leave as is or change it (e.g., `bhr-website`).
    *   **Production Branch**: `master`.
    *   **Framework Preset**: Select "Next.js (Static HTML Export)" OR "None". Ideally, select "None" and use the custom command below.
    *   **Build Command**: `npm run pages:build`
    *   **Build Output Directory**: `.vercel/output/static` (Crucial!)
5.  **Environment Variables (Optional but Recommended)**:
    *   Add a variable `NODE_VERSION` with value `20` (or higher) if needed, though Cloudflare usually picks up the right one.
    *   Under "Compatibility flags", ensure `nodejs_compat` is added if prompted, or set it in `wrangler.toml` if you were using Wrangler locally. For dashboard deployment, usually you just need the build settings.

## Important Notes

*   This setup uses the `@cloudflare/next-on-pages` adapter which allows server-side features of Next.js to work on Cloudflare Pages.
*   If you encounter issues with images, ensure `images.unsplash.com` is accessible and configured correctly in `next.config.ts` (already done).

## Troubleshooting

If the build fails:
1.  Check the logs in Cloudflare Dashboard.
2.  Ensure you selected the correct Build Output Directory: `.vercel/output/static`.
3.  Ensure the Build Command is `npm run pages:build`.
