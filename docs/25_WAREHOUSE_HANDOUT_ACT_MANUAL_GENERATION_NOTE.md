# 25 Warehouse — Handout Act Manual Generation Note

## 10.163. Manual generation of the handout act

Decision: if the handout act is enabled in warehouse settings, it should still be generated manually by button.

Rules:
- the system should not automatically create the handout act after every handout;
- the user generates the act when the document is actually needed;
- the action can be shown as `Generate handout act` or similar;
- if the act setting is disabled, the button can be hidden or unavailable.

Purpose:
- avoid producing unnecessary documents;
- keep the warehouse workflow lighter for small teams;
- let the user decide when a formal document is needed.

MVP approach:
- add a manual action/button for handout act generation;
- use the current warehouse handout data to build PDF/print;
- keep the act internal;
- store generated document metadata if document storage is enabled later.
