# BitMart

BitMart is a global cryptocurrency exchange providing REST and WebSocket APIs for spot trading, perpetual futures contracts, margin trading, real-time market data, and account and withdrawal management.

**Developer Portal:** https://developer-pro.bitmart.com/

## APIs

| API | Base URL | Description |
|-----|----------|-------------|
| Spot Trading | https://api-cloud.bitmart.com | Spot market orders, market data, algo orders, fees |
| Spot WebSocket | wss://ws-manager-compress.bitmart.com | Real-time spot market data and account events |
| Futures Trading | https://api-cloud-v2.bitmart.com | Perpetual futures orders, positions, funding rates |
| Futures WebSocket | wss://openapi-ws-v2.bitmart.com | Real-time futures market data and account events |
| Margin Trading | https://api-cloud.bitmart.com | Isolated margin orders, borrowing, and repayment |
| Account and Wallet | https://api-cloud.bitmart.com | Deposits, withdrawals, balances, transaction history |

## Authentication

BitMart uses HMAC-SHA256 request signing. All requests require:
- `X-BM-KEY` — API access key
- `X-BM-TIMESTAMP` — Current timestamp in milliseconds
- `X-BM-SIGN` — HMAC-SHA256 signature of `timestamp#memo#body`

Public endpoints require no authentication. KEYED endpoints require only the API key header. SIGNED endpoints require all three headers.

## SDKs

| Language | Install |
|----------|---------|
| Python | `pip install bitmart-python-sdk-api` |
| Node.js | `npm install @bitmartexchange/bitmart-node-sdk-api` |
| Go | `go get github.com/bitmartexchange/bitmart-go-sdk-api` |
| Java | Maven: `io.github.bitmartexchange:bitmart-java-sdk-api` |
| PHP | `composer require bitmartexchange/bitmart-php-sdk-api` |

## Rate Limits

Rate limits vary per endpoint and scope:
- **IP scope:** Public and keyed endpoints, typically 8–15 requests per 2-second window
- **KEY scope:** Authenticated query endpoints, up to 50 requests per 2-second window
- **UID scope:** Signed trading endpoints, up to 40 requests per 2-second window
- **General baseline:** 600 requests per 60 seconds where no specific limit is documented

Rate limit usage is exposed in response headers: `X-BM-RateLimit-Remaining`, `X-BM-RateLimit-Limit`, `X-BM-RateLimit-Reset`. HTTP 429 is returned when limits are exceeded.

## Pricing

API connectivity is free. Trading fees are charged per transaction:
- **New API users:** 30-day VIP3 trial with 0% spot trading fees
- **Standard (Class-A pairs):** 0.10% maker and taker
- **VIP tiers:** 12 levels based on BMX token holdings; fees as low as 0.04% maker / 0.045% taker at VIP12
- **BMX discount:** 25% fee reduction when paying fees in BMX (not combinable with API VIP program)

## Resources

- [API Reference (Spot)](https://developer-pro.bitmart.com/en/spot/)
- [API Reference (Futures)](https://developer-pro.bitmart.com/en/futuresv2/)
- [Quick Start & SDKs](https://developer-pro.bitmart.com/en/quick/)
- [Signature FAQ](https://developer-pro.bitmart.com/en/faq/)
- [GitHub Organization](https://github.com/bitmartexchange)
- [Telegram API Club](https://t.me/bitmart_api)
