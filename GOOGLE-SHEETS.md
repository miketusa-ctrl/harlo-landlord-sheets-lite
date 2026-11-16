# Using Harlo Landlord Sheets Lite in Google Sheets

> Templates, not tax, legal or accounting advice. Consult a CPA/attorney and follow your local landlord-tenant law.

## Option A — Import the .xlsx (recommended)
1. Open Google Drive → **New → File upload** → choose `Harlo-Landlord-Sheets-Lite-v0.1.0.xlsx`.
2. Right-click the uploaded file → **Open with → Google Sheets**.
3. **File → Save as Google Sheets** to get a native copy (the original .xlsx stays untouched).
4. Check the sample: Rent Roll shows one property (**Birchwood Fourplex**) with four units — two Paid, one Partial, one Vacant — and Tenant Ledger has running balances for Priya and Marco.

Dropdowns, conditional colors, frozen headers and filters carry over. No macros or Apps Script are used. Lite has only three tabs: Rent Roll, Tenant Ledger, and Disclaimer (no Portfolio Dashboard).

## Option B — Recreate key formulas (row 4 = first data row)
| Tab | Column | Formula |
|---|---|---|
| Rent Roll | Balance Due (H) | `=IF(C4="",0,MAX(0,D4-G4))` |
| Rent Roll | Status (I) | `=IF(C4="","Vacant",IF(G4>=D4,"Paid",IF(G4>0,"Partial","Unpaid")))` |
| Tenant Ledger | Signed (F) | `=IF(OR(C4="Charge",C4="Late Fee"),E4,-E4)` |
| Tenant Ledger | Running Balance (G) | `=SUMIF(A$4:A4,A4,F$4:F4)` |

Copy formulas down. Format date columns as dates (Format → Number → Date).

## Tips
- Keep one property on the Rent Roll in Lite. For multi-property dashboards, late-rent tracking, maintenance, leases, deposits, expenses and inspections, use **Harlo Landlord Sheets Pro**.
- Leave blank rows ready for new units or ledger lines; formulas already cover the sample range.

Google Sheets is a trademark of Google LLC. Harlo is not affiliated with or endorsed by Google.
Support: digitalpromohub.support@gmail.com
