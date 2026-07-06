# RouterLink Model Comparison

A single-file web app that compares and sorts RouterLink models using the `/api/v1/models/group` data, and provides the integration details (Base URL, Model, API format) for any selected model.

## How to run

Double-click `index.html` to open it in a browser (no server needed). On load, it automatically calls `GET {base}/v1/models/group` with the default **API Base URL** (`https://router-link.world3.ai/api`) and fills the table. If the API moves, just change the Base URL field at the top and click "Load models".

## Features

1. **Compare (up to 3)** — Select up to 3 models via checkboxes to see Context Length, Max Output, and per-modality Input/Output pricing (USD and $WAI) side by side.
   - Click a row (or drag with the left button held) to multi-select / deselect.
   - The **✕** button above the checkboxes (or "Uncheck all" in the compare panel) clears the selection.
   - Deprecated models are excluded from the list automatically.
2. **Sort (asc/desc)** — Click a column header (Context Length, Max Output, each token-type price, Model, Vendor, etc.) to toggle ascending/descending. The active column is highlighted with ▲/▼.
   - The compare panel appears to the **right** of the table; drag the splitter between them to resize it (width is remembered).
   - Use the **Columns** toggles to show/hide the Vendor and Provider columns.
   - Both the model table and the compare grid have top **and** bottom horizontal scrollbars when content overflows. The checkbox and Model columns stay frozen while scrolling.
3. **Integration** — Selecting a model shows the details needed to use it in another tool/SDK, each with a copy button. Missing values show `—`; a `*` marks tiered pricing (hover the `*` for the full tier breakdown). When multiple models are selected, identical fields are grouped under **Common** and only the differing ones (mainly Model) are shown per model.
   - **Format** — API format (e.g. `OpenAI Chat Completions (OpenAI-compatible)`)
   - **Base URL** — for an OpenAI-compatible SDK's `base_url` (`{endpoint}/v1`)
   - **Chat endpoint** — the full call URL (`{endpoint}/v1/chat/completions`)
   - **Model** — the exact routing string to pass as `model`
   - **Auth header** — `Authorization: Bearer YOUR_API_KEY`

## Integration info (example)

Selecting a model shows something like this (OpenAI-compatible SDK):

```
Format        : OpenAI Chat Completions (OpenAI-compatible)
Base URL      : https://router-link.world3.ai/api/v1
Chat endpoint : https://router-link.world3.ai/api/v1/chat/completions
Model         : world3-router-north-america/google/gemini-3.1-pro-preview
Auth header   : Authorization: Bearer YOUR_API_KEY
```

- With the OpenAI Python SDK, for example, put Base URL into `base_url`, the Model string into `model`, and your issued key into `api_key`.

## Notes

- Data source: https://docs.routerlink.ai/basics/models
- The Base URL and the compare-panel width are saved in the browser's localStorage (kept across revisits in the same browser).
