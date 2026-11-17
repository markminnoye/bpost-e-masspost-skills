> **When to use this file:** When choosing between OptiAddress (`MailingCheck`), the Address Proofing REST API, the public validation website, or the Address File Tool (AFT) upload path.

# Which address validation product?

These are **different bpost products**. Do not mix endpoints, auth, field models, or error codes.

| Use this | When | Protocol | Names / PII |
|---|---|---|---|
| **OptiAddress** (`MailingCheck` / MCP `check_batch`) | Mailing list validation with **corrections / suggestions** (thousands of rows), independent of deposit | XML/TXT mailing file (`MailingCheck`) | Recipient names **required** (real mailing) |
| **Address Proofing API** | Realtime check or Belgian label, 1–100 addresses; official street/city + **suggestions** | REST JSON to `api.mailops.bpost.cloud`, `x-api-key` | **Never send person names or other PII**; company name allowed |
| **Website** | Human one-off check | http://bpost.be/validationadresse | User types in the browser |
| **Address File Tool (AFT)** — **not** a validation product | Portal Excel/CSV upload to **create** a Mail ID / Round & Sequence mailing list | XLS/CSV via e-MassPost AFT UI | Same address data as a mailing create |

{% hint style="danger" %}
**AFT ≠ OptiAddress.** Agents must not expect AFT to return address corrections or alternative proposals. AFT responses add barcodes / sorting info and a `FEEDBACK` **status code**. Corrections and proposals come only from **OptiAddress** (`MailingCheck`, e.g. `7001` / `compCorrection`) or **Address Proofing**. See [address-file-tool.md](../schemas/address-file-tool.md) and [optiaddress-flows.md](../flows/optiaddress-flows.md).
{% endhint %}

## Decision

```
Need a Mail ID mailing list / deposit upload via portal Excel?
  yes → AFT (schemas/address-file-tool.md) — barcodes/sorting/FEEDBACK codes only
Need corrections or suggestions on a mailing list?
  yes → OptiAddress (flows/optiaddress-flows.md)
Need official street/city, suggestions, or S42 label lines (small set)?
  yes → bpost-address-proofing skill (Mailops REST)
Human only?
  yes → validationadresse website
```

## Do not confuse

| | OptiAddress | Address Proofing | AFT |
|---|---|---|---|
| Purpose | Validate + **correct / suggest** addresses | Realtime proof + **suggestions** / labels | Upload mailing list (create path) |
| Fields | Mail ID Comp codes 1–19, 90–93 | CEN/UPU S42 (`StreetName`, …) | Same Comp columns as mailing create |
| Errors / feedback | MID-4xxx, live `7001` / `compCorrection` | `address_not_recognized`, `missing_field`, … | `FEEDBACK` codes (e.g. MID-4030 / MID-4010) |
| Batch | Large files | Max **100** per call | Large files (portal limits) |
| Auth | e-MassPost customer/account | `x-api-key` (request: addressvalidation@bpost.be) | e-MassPost portal login |

Comp ↔ S42 mapping (and which Comps may go to Proofing): [addressing-rules.md](addressing-rules.md).

Proofing privacy (deny-list): skill `bpost-address-proofing`, file `reference/privacy-redaction.md`.
