# Full-Stack Intern Coding Challenge - Issues Found and Fixed

## Overview
This document outlines the bugs identified and resolved during the full-stack internship coding challenge. The project involved troubleshooting and fixing various issues in the application stack to ensure proper functionality.

## Bugs Found and Fixed

### Bug 1: Missing Dependencies
**Description:** The project had missing or incompatible dependencies during the `npm install` process.

**Fix:**
- Ran `npm install --legacy-peer-deps` to resolve dependency conflicts
- Updated `package.json` to ensure all necessary dependencies were included

### Bug 2: Deprecation Warning in Express URL Encoding
**Description:** The Express `urlencoded()` middleware was throwing a deprecation warning due to a missing `extended` option.

**Fix:**
- Updated the Express URL encoding configuration in `src/index.ts`:
  ```typescript
  app.use(express.urlencoded({ extended: true }));
  ```

### Bug 3: Database Connection Failure
**Description:** Initially, the backend was unable to establish a connection to the local PostgreSQL database due to incorrect credentials or missing environment variables.

**Fix:**
- Ensured the `.env` file contained correct credentials (`DB_USER`, `DB_PASSWORD`, etc.)
- Corrected the database connection string and verified the database was running locally

### Bug 4: Incompatible PostgreSQL Version
**Description:** The `pg` version was incompatible with the version required by `typeorm`, causing conflicts during installation.

**Fix:**
- Installed the required `pg` version:
  ```bash
  npm install pg@^8.5.1
  ```

### Bug 5: CORS Issues
**Description:** Cross-Origin Resource Sharing (CORS) issues arose when the backend API was accessed from the frontend, especially during local development.

**Fix:**
- Installed and configured the CORS middleware:
  ```bash
  npm install cors
  ```
- Added CORS middleware to the `src/index.ts` file:
  ```typescript
  import cors from 'cors';
  app.use(cors());
  ```

### Bug 6: Firewall Blocking Connection
**Description:** The local firewall was blocking the connection, causing issues with the application.

**Fix:**
- Configured the firewall to allow the backend service to connect to the necessary local services

### Bug 7: Webpack Version Compatibility Issue
**Description:** The project required a specific version of Webpack, which caused compatibility issues during the build process.

**Fix:**
- Installed the correct version of Webpack to resolve the versioning conflict:
  ```bash
  npm install webpack@4.46.0
  ```

## Conclusion
With these fixes implemented, the backend API is now running smoothly on port 3000, and all issues have been addressed. The application is fully functional and can interact with the local PostgreSQL database and the frontend without encountering major issues.
