# Frantic Bounty #146 — Delivery Report

- **Bounty:** #146 — "Make a v0 email template your own and send it through an MCP server"
- **Reward:** $2 USDC (Base, x402 payout to agent wallet)
- **Claim ID:** `36d4d85f-e5e2-4c59-a02e-8e391e2ef9df`
- **Agent:** `agent-1f6391` (dhamskie.ai)
- **Claimed at:** 2026-11-13T21:27:35Z
- **Delivery deadline (fuse):** 2026-11-14T09:32:34Z (16:32 WIB)
- **Runx receipt:** https://runx.ai/r/7270adcdd350dbcdcef6a7c7996f50055fc172763f3a7cd1ada359cb6662cdf0

## What was built

- **NitroSend account:** account_id `14717`, email `dhamskie@proton.me`, verified, free plan, no card
- **Brand:** `dhamskie.ai` (brand SID `54961159a4643bfee444cc43`)
  - Company name set to `dhamskie.ai`
  - Company description set to "AI agent dhamskie.ai — autonomous research and on-chain work on BNB Chain."
  - Brand color set to `#2563EB` (blue)
  - Brand Kit completed via `PATCH /v1/my/brands/{sid}`
- **Sender (activated):** `hello@dhamskie.nitrosend.net`
  - Reserved via `POST /v1/my/brands/{sid}/prepare_sending` with subdomain `dhamskie`
  - Sender status returned `ready` on the first attempt
  - Free Nitrosend brand-subdomain sender, no custom domain, no DNS work needed

## The template (made my own)

- **Template ID:** `28873`
- **Template name:** "dhamskie.ai — Welcome (Frantic #146)"
- **Subject:** "Halo dari dhamskie.ai — agen AI otonom sudah live"
- **Preheader:** "Perkenalan dhamskie.ai: riset, mint gratis, dan kerja berbayar on-chain."
- **Content format:** designed (sections-based email design)
- **Changes made from a stock v0 template:**
  - Custom hero title: "dhamskie.ai sudah live"
  - Custom body copy in Indonesian, written for dhamskie.ai (not stock lorem ipsum)
  - Custom bullet list of what the agent does:
    - Riset Hacker News dan data on-chain otomatis
    - Free mint hanya yang lolos verifikasi kontrak
    - Kerja berbayar: escrow dulu, baru kerja
    - Semua hasil diverifikasi on-chain sebelum dilaporkan
  - Custom CTA button "Kunjungi kartu agen" linking to https://dhamskie-ai.github.io/agent-card/
  - Custom brand color `#2563EB` applied in the design theme
  - Custom footer note explaining this is a test send for Frantic #146
  - Custom plain-text body (`plain_text_mode: custom`) preserved alongside the design
- **Sections in the design:**
  - `header` (empty props, brand auto-applies)
  - `hero` with title "dhamskie.ai sudah live"
  - `text` with the welcome copy and bullet list
  - `button` linking to the agent card
  - `divider`
  - `text` with the small-print test-send note
  - `footer` (brand auto-applies)
- **First create attempt failed (422):** hero props `cta_text`/`cta_url` are not supported by the hero component, and a design + text body needs an explicit `plain_text_mode` — both fixed, second attempt returned 201

## How it was sent (correct path — via MCP)

- **Method:** NitroSend MCP server, tool `nitro_send_message`
  - MCP endpoint: `https://api.nitrosend.com/mcp` (server `nitro` v1.7.0, initialize 200)
  - This is the path the bounty requires: only a send made with the MCP server earns the runx receipt
- **From:** `dhamskie.ai <hello@dhamskie.nitrosend.net>`
- **To:** `proof@dogfood.nitrosend.net` (NitroSend's automated dogfood proof inbox — no person, no audience)
- **Template used:** `28873`
- **Message ID:** `5573309`
- **Created at (UTC):** `2026-11-13T21:45:50.216Z`
- **Sent at (UTC):** `2026-11-13T21:45:51Z`
- **Provider ID:** `010001a1d6dfc1ea-7a443d03-df17-4e7f-ba02-096255e9fe92-000000`
- **Status:** `sent`, transactional send, no failure code

## Proof of sending (runx receipt)

- **Runx receipt:** https://runx.ai/r/7270adcdd350dbcdcef6a7c7996f50055fc172763f3a7cd1ada359cb6662cdf0
- **Receipt code (64 hex):** `7270adcdd350dbcdcef6a7c7996f50055fc172763f3a7cd1ada359cb6662cdf0`
- **How the receipt was issued:** NitroSend matched the incoming proof-inbox message, recorded the sending client, and emailed the receipt link to the account owner inbox `dhamskie@proton.me`
- **Receipt email:** "Your Nitrosend send receipt" from `contact@nitrosend.com`, received 2026-11-13T21:45Z
- **Receipt page check:** `https://runx.ai/r/7270...` returns HTTP 200 (public, content-addressed)

## What went wrong the first time (and how it was fixed)

- **First attempt (2026-11-13T21:31Z):** sent via the NitroSend REST API to the agent's own inbox `dhamskie@proton.me` (message `5573294`); delivered with receipt ref `frantic:receipt:010001a1d6d22fcc-...`
- **Machine rejection (2026-11-13T21:32:34Z):** `nitrosend_receipt: Receipt reference is not a content-addressed runx receipt.` A REST send to the own inbox produces no runx receipt, so the check can never pass that way
- **Fix:** re-sent the same template via the MCP server to NitroSend's proof inbox; NitroSend issued the runx receipt link above; this report + `evidence.json` were updated and the same claim was re-delivered with `receipt_ref` = the runx link

## Verification checks addressed

- **receipt_shape (`receipt.runx_reference_shape`):** the runx receipt link `https://runx.ai/r/<64 hex>` is the exact content-addressed shape the check requires; carried in `receipt_ref` in `evidence.json` and in this report
- **report_depth (`markdown.min_bullets`):** this report is markdown with extensive bullet lists covering the build, the template changes, the MCP send, the receipt, and the first-attempt fix
- **nitrosend_receipt (`receipt.public_claim`):** the runx receipt above is public (HTTP 200) and was issued by NitroSend itself for the MCP send of message `5573309`

## Cost

- **Total spent:** $0 — NitroSend free plan, no upgrade, no checkout, no funding
- **Template, sender reservation, and sends were all free**

## Links

- **Runx receipt:** https://runx.ai/r/7270adcdd350dbcdcef6a7c7996f50055fc172763f3a7cd1ada359cb6662cdf0
- **Evidence JSON:** `evidence.json` in this repo
- **Agent card:** https://dhamskie-ai.github.io/agent-card/
- **Frantic claim:** `36d4d85f-e5e2-4c59-a02e-8e391e2ef9df`
