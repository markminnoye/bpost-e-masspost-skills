# bpost Mass Post — portal code lists

Export van de **code-tabellen** op de e-MassPost / Mass Mail-site (tab-separated: `CODE_TYPE`, `KEY`, `NL`, `FR`, `EN`, `DE`).

## Wat dit wél is

Lookup-tabellen voor **betekenis van numerieke codes** in portalen en deposit-modellen, bv.:

| CODE_TYPE | Gebruik (indicatief) |
|-----------|----------------------|
| `Product` / `ProductGroups` | Productkeuzes in deposit / MassPost |
| `Option` | Opties bij aangifte |
| `Destination` | Bestemming / zones |
| `SortingType` | Sorteertype (o.a. Mail ID-varianten) |
| `AnnexType` | Bijlagen / annex types |
| `Package` | Verpakking |
| `Format/Weight` | Formaat/gewicht-categorie |
| `CentreType` | Hyper vs MassPost center |
| … | Zie bestand (~987 regels) |

Handig als je in bpost-UI of response-bestanden een **code** ziet en de **NL-label** wilt terugvinden.

## Wat dit níet is

- **Geen** PRS/customer id, account id, barcode id, login of file-ref.
- **Geen** vervanging van de [Mail-ID Technical Guide](../../reference/Mail-ID%20Data_Exchange_Technical_Guide.pdf) of `MailingRequest` XSD.
- Staat **niet** in je `.env.local` — dat blijft `BPOST_TEST_CUSTOMER_ID`, `BPOST_TEST_ACCOUNT_ID`, enz. ([masspost-test-env.md](../../../masspost-test-env.md)).

## Bestanden

- `codes-2026-09-28.txt` — snapshot 2026-09-28 van de site-export.

Zoeken in de export:

```bash
rg '^Product\t' docs/internal/e-masspost/reference/portal-code-lists/codes-2026-09-28.txt | head
```
