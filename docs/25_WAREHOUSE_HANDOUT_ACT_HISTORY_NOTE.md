# 25 Warehouse — Handout Act History Note

## 10.164. History of generated handout acts

Decision: generated handout acts should have history. Each generated act is stored as a separate record or version.

Rules:
- store who generated the act;
- store generation date and time;
- link the act to the project and warehouse handout operation;
- store document number or internal document ID;
- if a PDF file exists, store a link to it;
- if the act is generated again, do not silently overwrite the previous one;
- repeated generation creates a new version or record.

Purpose:
- allow opening the same act later;
- keep a reliable internal document trail;
- make it clear which document version was generated at which time;
- avoid losing earlier generated documents.

MVP approach:
- create a document history entry for every generated handout act;
- store metadata even if file storage is not ready yet;
- when file storage exists, attach the PDF link to the history entry;
- keep the handout act internal.
