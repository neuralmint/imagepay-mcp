# ImagePay MCP

An [MCP](https://modelcontextprotocol.io) server that exposes the **ImagePay x402 marketplace** — 40 paid API tools — to any MCP-capable agent.

## What it does
Each tool is gated by an [x402](https://x402.org) micro-payment on Base. Call a tool; the server returns a 402 with signed payment terms; your x402-enabled client pays per call. No API key, no subscription, no signup.

## Tools (40)
- **OCR** — image → text
- **PDF** — text, metadata, page split, merge
- **Image** — filters, transforms, QR generate/decode, palette, perceptual hash, face-detect, crop, resize, watermark, EXIF read/strip
- **Tabular** — csv↔json, xml→json, yaml→json
- **Web** — URL metadata (title/description/OpenGraph)
- **Utilities** — JWT decode, cron-next, unit conversion, slugify

## Endpoint
```
https://making-absurd-felt-tip.ngrok-free.dev/mcp
```
Transport: streamable HTTP. A bare MCP client `initialize` + `tools/list` returns all 40 tools. Unpaid calls return x402 payment terms (the server is Bazaar-native under resource type `mcp`).

## Using it
Point any x402-aware MCP client at the URL above. Example (TypeScript SDK):
```ts
import { Client } from "@modelcontextprotocol/sdk/client/index.js";
// connect to https://making-absurd-felt-tip.ngrok-free.dev/mcp
```

## Self-hosting
The upstream server is open-source (Hermes Agent project). This repo only holds the registry metadata; the live service runs elsewhere.

## License
MIT
