# MCP usage log

Run date: 2026-06-26  
Agent: Grok multi-MCP Prime Day resale tracker test

## Firecrawl

| Tool | Purpose | Outcome |
|------|---------|---------|
| `firecrawl_search` | Find public Prime Day deal pages | OK — WIRED, CR, PCMag, NBC, YouTube |
| `firecrawl_scrape` | WIRED under-$100 deals (JSON) | OK |
| `firecrawl_scrape` | Consumer Reports tech deals (JSON) | OK |
| `firecrawl_scrape` | PCMag day-3 deals | **Failed** — site not supported |
| `firecrawl_scrape` | NBC Select Prime Day deals (JSON) | OK |

Not used: crawl, agent, extract (scrape JSON sufficient).

## Google Sheets

| Tool | Purpose | Outcome |
|------|---------|---------|
| `sheets_get_metadata` | Confirm existing spreadsheet + Items tab | OK — title Prime-Day-Grok-Test |
| `sheets_insert_sheet` | Add **Price History** | OK |
| `sheets_insert_sheet` | Add **Summary** | OK |
| `sheets_batch_update_values` | Write Items, Price History, Summary | OK — 8 items, 16 history rows, 8 summary rows |
| `sheets_create_chart` | Optional chart | Skipped (data-first; can add later on Summary) |

Spreadsheet ID: `1j-dRfrY7ZK0mpwTy0RsmyQOeQhs9XGxp5sHjaoHcZhk` (user-provided; not created by agent).

## GitHub

| Tool | Purpose | Outcome |
|------|---------|---------|
| `get_me` | Resolve owner login | `brianjames-dev` |
| `create_repository` | `prime-day-resale-tracker-mcp-test` | OK — public |
| `push_files` | README + docs/* | OK |
| `issue_write` (create) ×3 | Follow-up issues | See issues on repo |

## Blocked / limitations

1. **PCMag** blocked by Firecrawl policy — used NBC Select instead to stay within URL budget.
2. **No live Amazon PDP prices** — public editorial only; prices may lag.
3. **List prices are proxies** for post-PD market until real `market_check` rows are appended.
4. **Fees not modeled** (eBay/Amazon resale, shipping, tax).
5. **Secrets:** did not open or commit service-account key files; Sheets access via host MCP + shared SA email only.
6. **Vercel MCP** unavailable (auth) — not required for this test.

## Local workspace note

Tracker notes live under `sandbox/repos/prime-day-resale-tracker-mcp-test/` in agent-eval-lab (not lab root).
