# Embedding the ISHR interactive charts in WordPress

`ishr-ga-cuts.html` contains the complete article and is updated alongside `embed.html` when charts change.

Use **GitHub Pages**, not the `github.com` source-code URL or `raw.githubusercontent.com` URL. The new `embed.html` provides a chart-only view, so the article text can remain in WordPress.

## Enable GitHub Pages

1. Open **Settings → Pages** in this repository.
2. Under **Build and deployment**, choose **Deploy from a branch**.
3. Select **main** and **/ (root)**, then click **Save**.
4. After publishing, open [the Roadmap chart](https://clee-ishr.github.io/ishr/embed.html?chart=roadmap) to confirm it is live.

## WordPress HTML block

Paste the following into a **Custom HTML** block *where you want a chart to appear*, replacing `roadmap` with a chart key from the table below.

```html
<iframe
  title="Special Procedures reporting cuts compared with the Roadmap"
  src="https://clee-ishr.github.io/ishr/embed.html?chart=roadmap"
  width="100%"
  height="330"
  loading="lazy"
  style="display:block;width:100%;max-width:100%;border:0;"
></iframe>
```

## Chart addresses and suggested iframe heights

These heights are **desktop starting values**, not measured guarantees. The complete WordPress HTML uses CSS breakpoints at 720px and 420px to allocate more height to wrapped tables and recommendations. Cross-origin iframe content cannot auto-resize without approved code in WordPress, so confirm no clipping or excess space in a published preview.

| chart key | Chart | Suggested iframe height |
|---|---|---:|
| mandates | Number of thematic mandates, 2014–2026 | 405 |
| events-table | New, merged and discontinued mandates since 2014 | 670 |
| reporting | HRC and General Assembly reports | 550 |
| renewals | Renewed mandates with reduced reporting | 490 |
| affected-table | Mandates whose reporting obligations were reduced | 1600 |
| unaffected-table | Mandates without reporting reductions | 1450 |
| cuts | General Assembly reports cut by session | 335 |
| roadmap | Reports cut compared with Roadmap indicative range | 330 |
| clusters | Reporting cuts by thematic cluster | 530 |
| core-groups | Core groups involved in reporting changes | 300 |
| periodicity | Reporting periodicity: six-year interactive comparison | 680 |
| waffle | Mandates affected, illustrated as a waffle chart | 310 |
| recommendations | Interactive five-point recommendations checklist and progress bar | 790 |
| all | All nine charts only (for preview, not recommended as one iframe) | 4400 |

Example: `https://clee-ishr.github.io/ishr/embed.html?chart=reporting`

**WordPress has 13 iframe placements** in the full article: nine chart views, three data-table views and one recommendations checklist. The three data tables use responsive card layouts below 720px to avoid horizontal scrolling. The two mandate-status tables use the keys `affected-table` and `unaffected-table`. The historical events table uses `events-table`.

## Important permissions and limitations

- WordPress must **allow iframes**. On many installations this requires the `unfiltered_html` capability, or a site administrator to configure an approved embedding method. An iframe that is stripped on saving will not work even when the GitHub site works correctly.
- The chart scripts run on GitHub Pages, **outside** the WordPress page. You do **not** need to permit arbitrary JavaScript in WordPress merely to show an approved iframe.
- The source is a **public GitHub repository**. Do not commit unpublished or confidential information.
- Cross-origin iframes **cannot automatically set their own height in WordPress**. The embed sends an optional `ishr-chart-height` message, but using that message to resize requires site-side JavaScript and admin approval. For a no-JavaScript WordPress embed, set the iframe `height` manually.
- All chart visuals and underlying data remain in the existing HTML source. The chart-only view selects which chart to show using `?chart=`. Any further design edits should be made to `ishr-ga-cuts.html` **and copied into the embed viewer** until the files are refactored to use a single shared source.

## Editing and republishing

You can edit `embed.html` in GitHub and commit changes. The new version will be published by GitHub Pages if it is configured to deploy from `main`. Do not paste the D3 JavaScript into WordPress.
