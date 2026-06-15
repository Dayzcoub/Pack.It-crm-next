# 25 Warehouse — Return Act Problem Attachments Note

## 10.176. Problem attachments in the return act

Decision: if photos or files were added to problem rows during return acceptance, they should be shown in the return act.

Rules:
- problem row attachments are part of the internal return act;
- attachments should be connected to the related problem row;
- the return act may include photos, files, or references to stored attachments;
- if no attachments exist, no empty attachments block is shown.

Purpose:
- preserve visual evidence and related files in the return document;
- make problem rows easier to understand;
- avoid searching separately for photos added during return acceptance.

MVP approach:
- include problem-row attachments in the generated return act where available;
- keep the document internal;
- store files in the normal attachment storage and reference them from the return act.
