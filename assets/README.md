# assets/

Place the following files here before going live:

| File                        | Size          | Source                                                    |
|-----------------------------|---------------|-----------------------------------------------------------|
| app-icon.png                | 512×512 px    | Export from Xcode Assets (AppIcon 1024px, downscale)      |
| screenshot-savings.png      | 390×844 px    | Simulator screenshot — Savings screen (hero numbers)      |
| screenshot-panels.png       | 390×844 px    | Simulator screenshot — Panel Config + sun path chart      |
| screenshot-obstruction.png  | 390×844 px    | Simulator screenshot — Obstruction mapping / camera view  |
| screenshot-chart.png        | 390×844 px    | Simulator screenshot — Monthly usage vs. production chart |
| og-image.png                | 1200×630 px   | Social share card: app icon + hero screenshot side-by-side|

Replace the emoji placeholder divs in index.html with:
    <img src="assets/screenshot-savings.png" alt="Savings screen showing annual savings and break-even" class="screenshot-card">

The og-image.png is referenced in the Open Graph meta tags in index.html.
