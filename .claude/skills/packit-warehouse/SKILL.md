# PACK.IT Warehouse and Inventory Skill

Use this skill before implementing catalog, warehouse, stock, reservations, deficits, subrent, scanning, loading, return, or inventory movements.

## Main rule

Warehouse is not a static list. It is an operational system tied to project dates, reservations, movements, people, statuses, history and documents.

## Core concepts

```text
Catalog Item
  -> model/type/brand/category/specs/default price/rules

Asset / Stock Unit
  -> physical unit or counted stock item
  -> barcode/QR/RFID-ready identifier
  -> condition/status/location

Warehouse Movement
  -> receive / reserve / pick / load / return / repair / write-off / transfer

Reservation
  -> project + date range + required quantity + allocated stock + shortages
```

## Availability rules

- Availability must be date-aware.
- A project reservation must block or warn against conflicting reservations.
- Deficit/shortage is a first-class state, not only red text in UI.
- Subrent must be tracked as separate from owned stock.
- Substitutions must be explicit and auditable.
- Quick constructors may use ideal catalog logic; production estimate/CRM must use warehouse availability.

## Scanning workflow

MVP should support QR/barcode by phone camera before expensive RFID.

Required flows:

- mark item/unit;
- scan for project picking;
- loading confirmation;
- on-site issue/report;
- return confirmation;
- missing/damaged state;
- inventory count;
- movement history.

Future-ready flows:

- RFID labels;
- handheld terminals;
- gate scanning;
- NFC;
- automated discrepancy reports.

## Documents generated from warehouse data

- pick list;
- loading list;
- return list;
- deficit list;
- subrent list;
- damaged/missing report;
- inventory audit report.

These must be generated from the same reservation/movement data used by the project and quote.

## UI guidance

Warehouse mobile UI is not a smaller admin panel. It is a field tool:

- scan-first;
- large tap targets;
- offline-tolerant where possible;
- clear project/date/location context;
- fast discrepancy reporting;
- minimal text entry.

Desktop warehouse UI can be richer:

- stock matrix;
- reservations calendar;
- movement history;
- deficit dashboard;
- subrent management;
- label printing.

## Red flags

- Stock availability calculated only from current quantity without date ranges.
- Manual deficit text not tied to reservation records.
- Warehouse PDF generated from quote lines instead of reservation/BOM data.
- Scans that update UI but do not create movement records.
- Owned stock and subrent mixed without distinction.
