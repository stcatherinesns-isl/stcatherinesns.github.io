ISL MANAGEMENT HUB — STATIC FRONTEND (NO APPS SCRIPT HTML SERVICE)

WHY THIS VERSION IS DIFFERENT
The Apps Script frontend still used HtmlService, which means it still passed through
Google's userCodeAppPanel/OAuth-dialog HTML wrapper. Splitting out SpreadsheetApp
permissions did not remove that wrapper. This version is a plain static HTML page.
It contains no HtmlService, no google.script.run, and no SpreadsheetApp code.

The existing Apps Script ContentService backend remains responsible for all data,
PIN verification, authorisation, and database writes. It uses POST form submissions
plus read-only JSONP polling. This is specifically compatible with a static page on
another HTTPS host and does not require CORS headers.

FRONTEND FILES
  index.html   Upload this file to the root of the static website.
  .nojekyll   Keeps GitHub Pages from trying to process the site with Jekyll.

BACKEND
Your existing backend Apps Script deployment is already configured in index.html:
https://script.google.com/macros/s/AKfycbwSWYOYT7XI3j1lbQ9mJfD0UOYfWtV2fAZ_fbOFnM3EfvtbqbTTcrkORL--YxUuBv8/exec

Do NOT publish backend Code.gs, passwords, or spreadsheet contents in the static site.
Keep the backend Apps Script project private. Its deployed web app endpoint is public
because the app has a public shared dashboard; protected operations still require a
valid signed-in session and admin/member permissions are enforced server-side.

PUBLISH USING GITHUB PAGES
1. Sign in to https://github.com/ (create an account if needed).
2. Click + (top right) > New repository.
3. Name it: isl-management-hub
4. Set it to Public (GitHub Free requires a public repository for Pages).
5. Tick Add a README file, then Create repository.
6. In the new repository, choose Add file > Upload files.
7. Upload index.html and .nojekyll from this folder. Do not upload this README if you
   prefer to keep the repository minimal; it is only installation guidance.
8. Click Commit changes.
9. Open repository Settings > Pages.
10. Under Build and deployment, choose Deploy from a branch.
11. Select branch main and folder /(root), then Save.
12. Wait for the deployment to finish. Under the Pages section, click Visit site.
13. Bookmark/share the resulting https://YOUR-USERNAME.github.io/isl-management-hub/ URL.

GitHub's current official guide:
https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
Publishing-source guide:
https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

FIRST USE
1. Visit the new GitHub Pages site. It should load the ISL dashboard.
2. Sign in as Principal with the initial PIN 1234. The login page deliberately does not display the shared temporary PIN.
3. In Admin, enter names and initials for all five members and ensure the correct AP2
   member has administrator access (Principal should remain an administrator).
4. Change the initial PINs before sharing the URL with staff.
5. Test one duty, action, calendar event, task and draft check-in before full rollout.

SECURITY / PRIVACY
- The dashboard is deliberately public, as requested. GitHub Pages is also public. The page includes a noindex directive to discourage search indexing, but this is not an access control.
- The private member data is not stored in the website files; it remains in the Google
  Sheet accessed only by the Apps Script backend.
- Avoid placing sensitive pupil or personnel information in notes, event descriptions,
  or evidence links.
- Do not use the initial PIN 1234 for ongoing access. Change all PINs before sharing.
- The site repository contains the static page and backend endpoint URL. It does not
  contain the Apps Script source or the database itself.

UPDATES
To update the app interface in future, replace index.html in the GitHub repository and
commit the change. Backend changes continue to be deployed from Apps Script separately.
