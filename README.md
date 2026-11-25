# Signaldesk — Digital Product Studio V3

Standalone browser implementation reconstructed from the supplied Signaldesk screen recording and reference moodboard. The original Sites app is unchanged. This is an independent frontend, not a migration or deployed service.

## Run

Open `index.html` in a normal desktop browser, or serve the folder using `python -m http.server 8000` and open `http://localhost:8000`. No package installation, external font/image requests, build step or API key is required. For persistent storage, a normal HTTP origin is recommended; file viewers and sandboxed browsers may restrict localStorage and downloads. Mobile: extract the ZIP and open the HTML using a browser or host it on a static server.

## Implemented

- 13 views: Overview, Research board, Compare ideas, Prioritization, Product outline, Validation, Launch tracker, Decision log, Product generator, Design studio, Templates, Saved library, Settings/export.
- Research idea editing, evidence URL, checked date, price/currency, demand/competition labels, audience, fit, waitlist, sample notes, four draft AI-tool feasibility fields, weighted scoring. Seed ideas are unverified examples; not real marketplace demand measurements.
- 19 product categories with deterministic local templates: business/portfolio sites, Canva-style SVGs, social kits, planners, Notion Markdown, spreadsheet calculator, resume, FAQ, local web app, e-book, course, logo, mockup, invitation, presentation HTML, SVG icon pack, bundles.
- Live HTML/SVG preview, editable copy and blocks, six palettes and custom accent, style and format options where applicable, three visual variants, comparison and ZIP export. Some document formats share a common design layout; variants do not alter every feature in every category.
- Individual source files, PNG rasterization for SVG, ZIP packages, editable configuration JSON, version snapshots, duplicate, restore, delete, workspace backup/import and research CSV. HTML print layouts can be saved as PDFs via a browser's print dialog; no native PDF/XLSX/PPTX export.
- Original layered inline SVG icons, CSS studio lighting, rounded bento layout, keyboard focus, mobile navigation, reduced-motion support. All rendering assets are bundled inline.
- External Canva links and manual Canva handoff. An SVG is editable vector source, but importing into Canva may flatten it. Native Canva design generation requires an authenticated external integration; the app does not claim to make native editable Canva templates or template links.

## Verification performed

Chromium headless smoke test with HTML loaded into a test page (browser navigation policy blocked file/URL navigation in this environment). A test storage shim was used for desktop. Verified initial render, website preview content, one-click generation, edit/save revision, ZIP CRC/integrity, category output filenames for all 19 categories, social SVG preview and PNG download, three visual comparison cards, add idea, feasibility draft, validation and launch check, library records, and 390px viewport no horizontal document overflow. No uncaught JavaScript errors in that smoke test. Real persisted browser reload, all product templates visually audited at all sizes, full accessibility conformance, original database migration, and live integrations were not verified.

## Production integration checklist

1. Recover original Sites source, storage/API contracts, export existing records and write migration tests before replacing the live app.
2. Add authenticated server-side generation and job management with provider keys outside the frontend, schema validation, retries, quotas and output validation. The present creative brief is saved as metadata rather than sent to an AI model.
3. Connect authorized marketplace data sources with timestamped provenance, caching and source-specific terms; never synthesize sales counts.
4. Connect Canva with its supported authenticated workflows and verify each native design ID/edit URL, permissions, editable layers and template sharing rights.
5. Add account/database persistence, access controls, secure file storage, e2e and accessibility testing; audit every category's content, responsive layout and export before commercial sale.

Generated content is a starting template, not a guarantee of commercial readiness or marketplace acceptance. Replace illustrative copy and contact details and verify licensing/rights before distribution.
