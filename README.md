# Trip.com Flight Search

Search and compare Trip.com flights in Claude using an existing remote MCP server. This plugin supports fixed-date and flexible-date flight searches, including one-way and round-trip travel. It provides search guidance and connects to the flight results interface returned by the server. Booking, payment, order lookup, ticket changes and cancellations are outside its scope.

## Setup

The configured remote MCP endpoint is `https://fly.trip.com/flight/mcp/claude`, supplied by the service owner. This plugin uses only its flight tools. Verify connectivity and the exposed tool registry before directory submission.

In Claude chat and Cowork, connect the declared server in the plugin Connectors tab. In Claude Code, load this folder with `claude --plugin-dir /absolute/path/to/trip-flight-claude-plugin`.

## Examples

- Find flights from Shanghai to Tokyo on December 15, 2026.
- Compare round-trip fares from London to Singapore for December 10–17, 2026.
- Find low fares from Singapore to Tokyo during December 2026.

Prices and availability are search results and can change before booking. Open the returned Trip.com link to check the applicable fare and complete any booking.

## Data handling

This package contains only Markdown and JSON. It runs no local server, hooks, package installers or executable scripts and implements no local storage. Once connected, tool arguments, including route, travel dates, requested passenger details, language and search preferences, are sent to the configured Trip.com MCP service. That service may return an interactive results widget, load Trip.com resources and report service or widget analytics. Opening a returned link contacts the linked Trip.com site. Server-side logging, retention and privacy disclosures must be verified by the service owner for the directory submission; this package does not establish those policies. Do not provide passwords or payment credentials in search requests.

## Validation and directory submission

Run `claude plugin validate .` from this repository. This checks package syntax, not production connectivity or directory approval. Verify the endpoint and flight tools, test exact-date and flexible-date searches and the results widget, and confirm the applicable license and data-handling disclosures before directory review.

This repository is initially maintained on company GitLab. Anthropic currently requires a github.com repository for directory submission, public before publication. A separately operated remote MCP server must also be submitted as a connector if it has not already been submitted. See the [submission guide](https://claude.com/docs/plugins/submit) and [checklist](https://claude.com/docs/plugins/pre-submission-checklist).

## License

This plugin package is licensed under the [MIT License](LICENSE). This license applies to the files in this repository; it does not license the separately operated Trip.com service or its source code.
