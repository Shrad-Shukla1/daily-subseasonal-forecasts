# Subseasonal 30-day forecasts for Africa

A static GitHub Pages site showing the weekly bias-corrected, downscaled SubC precipitation
forecast maps for East (EA), West (WA) and Southern (SA) Africa: 30-day total, anomaly (mm)
and percent of normal. Sister site to `../dekadal-forecasts/`.

The maps are not stored here. The page loads them from
<https://data.chc.ucsb.edu/products/SubX/Plots/>, where the daily SubC pipeline
(`Derived_products/Process_and_plot_subseasonal_forecasts.py`) writes

    {Thursday}/{DOM}_total_rainfall[_anomaly|_pct_normal]_{Thursday}_to_{Thursday+30 days}.png

The data server does not allow other sites to read its folder listings, so `index.html`
builds these names itself. On load it finds the latest week by trying this Thursday's East
Africa map and stepping back a week at a time (up to `LOOKBACK_WEEKS`), then offers every
week back to `FIRST_WEEK`. **If the pipeline's file names or folder layout change, update
`mapUrl()` in `index.html` to match.**

Links can point at a region and week: `index.html#WA/2026-10-29`.

Nothing needs to be redeployed when new maps are published; the page picks them up.
To preview locally, open `index.html` in a browser.
