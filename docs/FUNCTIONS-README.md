# Shopify Functions (Concept)

`tiered-discount-input.graphql` defines the exact cart data that Shopify sends into the Function at runtime. Think of it as the input contract.

`tiered-discount-function.js` contains the business logic. It reads cart total amount, checks tier thresholds, and returns discount instructions for the best qualifying tier.

The Function does not directly edit cart values. Instead, it returns instructions because Shopify securely validates and applies discount operations on the platform side. This prevents unsafe client-side manipulation and keeps checkout behavior consistent.

In a real app, this logic is packaged in a Shopify app extension and deployed with Shopify CLI (for example: `shopify app deploy`). During deployment, Shopify compiles the Function to WebAssembly so it can execute very fast at checkout scale.
