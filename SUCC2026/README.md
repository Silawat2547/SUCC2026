# Shopee Delivery Success Engine

An interactive English-language case prototype with Operations and Buyer app workspaces. The buyer tracking interface follows the supplied mobile reference.

## Included source

| File | Purpose |
| --- | --- |
| `index.html` | Website entry point and page metadata |
| `style.css` | Desktop and mobile layouts, typography, and colors |
| `app.js` | Synthetic orders, UI rendering, interactions, and state |
| `.nojekyll` | Serve this package as static files on GitHub Pages |

No build, npm installation, backend, API key, or framework is required. All application source is included. Google Fonts is optional: system fonts are used if unavailable.

## Publish with GitHub Pages

1. Extract this ZIP on your computer. Do not upload the ZIP itself.
2. Create a GitHub repository (a public repository works with GitHub Free), or open your chosen repository.
3. Upload the extracted files to its top level. `index.html`, `style.css`, and `app.js` must be together at the repository root, not inside another folder. Review any existing files before replacing them.
4. Commit the upload to `main` (or your chosen branch).
5. Open **Settings > Pages**.
6. Under **Build and deployment**, choose **Deploy from a branch**.
7. Choose your uploaded branch and **/(root)**, then **Save**.
8. Open the published link shown in Pages once deployment succeeds.

The relative asset paths support repository-based URLs without editing the code. Uploading only this README or the ZIP will not publish the app.

Official guide: https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site

## Run locally

Open `index.html` in a modern browser. For a local HTTP server, run this command in the extracted directory if Python is installed:

```sh
python -m http.server 8000
```

Then visit http://localhost:8000. Clipboard access can depend on browser permissions and a secure context; GitHub Pages uses HTTPS.

## Suggested walkthrough

1. Open **Order workspace**, then select Emma Wilson's order ending in **250142**.
2. Click **Send readiness check**, then confirm **Send demo message**.
3. Switch to **Buyer app** at the top.
4. Confirm readiness or choose an available delivery round.
5. Return to **Operations** and inspect the updated readiness, slot, and activity trail.
6. Use **Operational outcome** to simulate dispatch, successful delivery, or an unsuccessful attempt.
7. Explore Sam Taylor's order for recovery, Drew Parker's order for a disputed attempt, and Robin Chen's order for return/refund tracking.
8. Use **Reset demo** to restore all eight sample orders.

## Working features

- Operations overview with sample cohort counts and risk distribution.
- Searchable order workspace with risk and status filters.
- Order details, illustrative risk factors, readiness checks, and audit trail.
- Buyer order list, tracking, readiness response, scheduling, contact edits, and support.
- Simulated voluntary digital payment and updated COD balance.
- Delivery outcomes, recovery, human review, and cancellation requests.
- Seller return receipt, refund completion, and loss/damage claim review.
- Pilot cohort comparison and CSV export of synthetic orders.
- Optional feature-detected WebMCP tools to read orders or navigate views.

## Prototype boundaries

- All buyers, orders, delivery history, and risk scores are fictional examples.
- Scores are seeded values, not predictions from a trained AI model.
- No real notifications, bank transactions, deliveries, refunds, or claims are sent.
- Operations and Buyer app share state only inside the current page. Different devices or browser tabs do not synchronize.
- Data is held in memory. Reloading the page or choosing Reset demo restores the sample orders.
- There is no authentication or server database in this package. Both roles are selectable for demonstration.
- The prototype allows at most two readiness messages per order and applies a two-attempt demo limit. Real limits require operational validation.
- Risk scores and silence alone do not authorize a hold or COD restriction.
- This is an independent case concept, not an official Shopee service.

## Editing the code

- Change sample buyers and orders in `seeds()` in `app.js`.
- Change the color palette and shared sizing in `:root` in `style.css`.
- Operations pages are rendered by `overview()`, `orderworkspace()`, `detail()`, `pilot()`, and `policies()`.
- Buyer screens are rendered by `buyer()`, `tracking()`, `buyerAction()`, `buyerOrders()`, `messages()`, and `support()`.
- Dialog interactions are handled by `action()` and `submitModal()`.
- Keep the shared state logic together so both roles show consistent updates.

## Troubleshooting

- **Blank page or missing styles:** Confirm all three application files were uploaded together and retained their names.
- **404:** Check that `index.html` is at the selected publishing root and that the deployment completed.
- **Old content:** Check the latest deployment and refresh the browser cache.
- **Buyer confirmation is missing:** Send a readiness message from Operations first, then open the same order in Buyer app.
- **Changes disappear:** This is expected on reload; the prototype has no persistent backend.

## Browser compatibility fix (revision 2)

Application code is isolated from browser globals, and the header renderer no longer uses the reserved `window.top` name. This resolves the blank-page startup failure. Replace the three application files together and reload after deployment.
