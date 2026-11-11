---
name: flight-search
description: Search and compare Trip.com flights for specific or flexible travel dates, including one-way and round-trip travel. Use for flight discovery and airfare comparisons, not existing bookings or other travel businesses.
---

# Trip.com flight search

## Choose the search

- Use the connected server's `search_flights` for a specific departure date, including cheapest-on-that-day requests.
- Use `search_low_price_flights_v2` for flexible, approximate or range-based dates. Use legacy `search_low_price_flights` only if v2 is unavailable and its schema is exposed.
- Read the available tool schema before constructing arguments. If routing or supported fields are unclear, call `flight_tools_intro` when available.
- If the connector or tools are unavailable, explain that it must be connected; do not fabricate a search or silently substitute another service.

## Collect and send inputs

Reuse route, dates and trip type already given. Ask concisely for missing required fields only. Resolve relative dates against the current conversation date and user timezone. Obtain the return date or return window for a round trip. Preserve named countries, cities, airports and explicit alternatives rather than guessing airport codes or expanding countries into cities.

Use date formats and defaults declared by the actual tool schema. For exact search, dates use `YYYYMMDD`; for flexible search follow its exposed range schema. Preserve the original user request in `rawQuery` only when accepted by the tool. Use en-US and USD where the schema permits a default and the user has not specified otherwise. Do not invent unsupported fields or search filters.

Represent round trips as reciprocal legs when the schema supports them. Do not combine unrelated one-way offers into a claimed round-trip ticket. Exact searches cover at most three resolved origin/destination pairs per call: explain any returned `odSearchCoverage.skippedOds` and offer a separate search for remaining pairs. Keep flexible search windows within the tool's declared limits. Ask before relaxing explicit hard requirements that the tool cannot enforce.

## Present the actual result

Use the tool-associated MCP results widget when supported by the host. Do not invent a rendering tool or treat its `ui://` resource URI as a web link. Do not claim successful rendering without evidence. If the host reports a rendering failure, state the limitation and offer the returned Trip.com links without manufacturing a replacement interface.

Keep the summary after a new search concise, normally within 50 words, covering the key outcome and material caveats. Preserve returned prices, currencies, travel dates, itinerary groupings, order and links. Do not invent availability, baggage allowances or fare rules. Treat absent facts as unknown. A fare search is not a reservation or a price guarantee.

For follow-up comparisons, use existing returned data and a focused Markdown table where useful. Do not repeat the search solely to reformat results. Distinguish empty results from tool errors. Correct schema validation errors before retrying; do not repeat invalid arguments unchanged.

## Scope

This plugin searches flights only. Do not claim to book, pay, retrieve private orders, change or cancel tickets, or search trains, hotels, cars or tours. Guide unsupported order questions to the relevant Trip.com order details or support. Never request passwords or payment credentials.
