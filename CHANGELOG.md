## V19.1 — 29 September 2026
### PDF pagination — rebuilt from V17
- **Base version is BEYDUN AGRO V17 — Translation Fixed**, the last version confirmed to load data correctly before the later technical changes.
- Re-applied only the warehouse inventory PDF pagination improvement requested by the user.
- Warehouse sections can now use remaining page space instead of forcing large blank areas.
- Table headers repeat when a table continues onto a new page.
- Individual rows are kept intact.
- Print margins and row spacing were reduced to fit more inventory rows per page.
- No changes were made to inventory quantities, prices, warehouses, sales, movements, returns, translation logic, backup logic, or application data.
- Service-worker cache version was advanced only to ensure the rebuilt application shell is loaded.

## V17 — 29 September 2026
### Arabic / Turkish translation audit
- Audited the language switching behavior across the application.
- Added a complete fallback pass that translates exact UI strings from the Arabic/Turkish translation catalog even when they are rendered outside `[data-key]`.
- Added missing common UI/category labels that were hard-coded outside the main translation catalog.
- Arabic mode keeps **drug names, packaging/unit text, and prices unchanged** as requested.
- Turkish mode translates the UI to Turkish while preserving **drug names, packaging/unit text, and prices**.
- Warehouse names continue to use their language-specific Arabic/Turkish fields.
- Added translation handling for placeholders, titles, and aria-labels when their values are part of the UI translation catalog.
- No inventory quantities, prices, drug names, packages, movements, sales, returns, audit records, or warehouse stock data were changed by this translation fix.

## V16 — 29 September 2026
### Warehouse control and unpriced medicines
- Enhanced **إدارة المستودعات / Depo Yönetimi** so every warehouse has a delete control.
- A warehouse can only be deleted when it contains no products; the application blocks deletion of a non-empty warehouse to protect stock data.
- The application also prevents deleting the final remaining warehouse.
- Added an **الأدوية غير المسعرة / Fiyatsız İlaçlar** filter in **إدارة الأسعار / Fiyat Yönetimi**.
- When enabled, the price page shows only products whose price is zero or empty, so they can be edited directly.
- The unpriced filter respects the V15 zero-stock visibility rule: zero-stock products remain hidden from normal price lists and searches.
- No stock quantities, movements, sales, returns, audit logs, or historical records were changed by this update.

## V15 — 29 September 2026
### Zero-stock visibility rule
- Zero-stock products (`qty = 0`) are now hidden from normal product lists and product searches throughout the application.
- This applies to inventory/warehouse lists, the all-products list, price/product lists, reports/product selection lists, dose/medicine selection lists, purchase product selectors, and other normal product pickers/searches.
- The dedicated **الأدوية المنتهية / Tükenen İlaçlar** list remains the exception and continues to show all `qty = 0` products.
- Historical records such as sales, movements, audit logs, returns, and other transaction history are not deleted or altered by this visibility rule.
- No stock quantities were changed.

# BEYDUN AGRO — CHANGELOG

## V14 — 29 September 2026
### Documentation / Release consolidation
- Consolidated the change history from the V7 baseline through V14.
- Documented the product-name, package/unit, price, and classification synchronization work.
- Documented the inventory-safety requirement: stock quantities, warehouse assignments, and historical transaction records were preserved during the synchronization work.
- Documented the Excel-based `HASTALIK-ZARARLI` classification synchronization.
- Recorded the five products for which no reliable `HASTALIK-ZARARLI` match was found and therefore no classification was guessed:
  - BOROPLUS
  - EFA LEAF
  - GAXY
  - SOL FERT — 1 LT
  - SOL FERT — 5 LT

## V13 — 29 September 2026
### HASTALIK-ZARARLI synchronization
- Synchronized the application's medicine-type/classification data with the `HASTALIK-ZARARLI` column in the Excel reference file `2027 SATIŞ FİYAT LİSTESİ.xlsx`.
- Matched 210 of 215 inventory/product records to a reliable Excel classification.
- Preserved the existing internal classification data as a compatibility layer rather than deleting it.
- Did not alter stock quantities, warehouse assignments, prices, or historical movement records as part of the classification update.
- Left five records without a guessed classification because no reliable Excel match was established:
  - BOROPLUS
  - EFA LEAF
  - GAXY
  - SOL FERT — 1 LT
  - SOL FERT — 5 LT

## V12 — 29 September 2026
### Selected package/unit corrections
Applied only the seven explicitly requested package/unit changes:
1. COCOLY: 20 KG → 25 KG
2. CARLOS: 1 KG → 2.5 KG
3. FASCINATE: 1 LT → 1 KG
4. ODEON: 1 KG → 800 GR
5. VITASEVE: 10 LT → 10 KG
6. ANTHOLOGY: PAKET → 600 GR
7. DEFENTOX: 0.25 ML → 250 ML

- No stock quantities were changed.
- No additional package/unit changes were applied beyond the seven requested changes.

## V11 — 29 September 2026
### Excel-based product name/package synchronization
- Updated product names to follow the names in the 2027 Excel price list.
- Updated package/unit descriptions while taking package size into account.
- Examples included:
  - AXLERON 250 ML → AXLERON 200 CC
  - COCOLY 20 KG → COCOLY 25 KG
  - CARLOS 1 KG → CARLOS 2.5 KG
  - ODEON 1 KG → ODEON 50 WP 800 GR
  - DEFENTOX 0.25 ML → DEFENTOX 250 ML
- Preserved inventory quantities during the name/package synchronization.
- The Excel list was used as the naming/package reference.

## V10 — 29 September 2026
### Price correction
- Corrected ANTHOLOGY price from 2,250 to 3,500 based on the 2027 Excel price list.
- Added update handling so previously stored data could receive the corrected price.
- No inventory quantity change was intended by this correction.

## V9 — 29 September 2026
### 2027 product-name alignment
- Updated product names to align with the 2027 Excel price list.
- The source changelog recorded 127 product-name changes and 74 already-matching names.
- Package values were intended to remain unchanged in that release.

## V8 — 29 September 2026
### 2026–2027 price update
- Updated sales prices for the 2026–2027 season according to the application's release history.

## V7 — baseline
- Baseline version used for the detailed V7 → later-version inventory comparison.
- Later synchronization work was designed to preserve stock quantities and historical operational records while updating descriptive/reference data.
