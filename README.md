# UOC E-Commerce — Practice 2 (2025–2026) — PrestaShop 8 “Coverage Pack”

## Context (READ THIS FIRST)

This repository is a **standard PrestaShop 8 installation** running locally (XAMPP / Apache / MySQL / PHP 8.1).  
Your mission (Codex) is **NOT** to build an e-commerce from scratch and **NOT** to replace PrestaShop core.

Your mission is to **configure and minimally extend** (only if needed) the base installation so the store **demonstrably covers Practice 2 points 1–4** via:
- Back Office configuration that enables the required behaviors
- A small “helper” module (optional) to make evidence easier (screenshots + exported settings)

This README is derived from the official practice statement. :contentReference[oaicite:0]{index=0}

---

## Non-Goals (STRICT)

- Do NOT modify PrestaShop core files (`/classes`, `/controllers`, `/src`, etc.)
- Do NOT install third-party themes
- Do NOT add non-required features
- Do NOT require real payment credentials (PayPal is *theoretical*)

If PrestaShop already does it, **use it**. If configuration is enough, **do not code**.

---

## Deliverables Codex Must Produce In This Repo

1) A **configuration checklist** at `docs/config_checklist.md` describing exactly:
   - where to click in Back Office
   - what to set
   - what to screenshot
   - what to test on Front Office

2) A **minimal evidence helper module** (optional but recommended) located at:
   - `modules/uoc_practice2/`
   - Purpose: provide a Back Office page that summarizes relevant config values and links to key admin pages, so screenshots are easy and consistent.
   - It must not change store behavior; it’s for visibility only.

3) A `.gitignore` entry (or update) to prevent committing local runtime/credentials:
   - ignore `/var/`, `/cache/`, `/log/`, `/config/settings.inc.php` if present, and any local override secrets.

---

## Required Test Data (So Screenshots Aren’t Empty)

Codex must ensure the store contains **minimum content**:
- At least **3 categories** (e.g., “Cameras”, “Film”, “Accessories”)
- At least **6 products** spread across categories
- At least **one out-of-stock product** (stock = 0) to demonstrate stock behavior
- Shipping enabled with at least **one carrier** (default is fine)
- Taxes configured at least at a basic level (default is fine if present)

If the installation wizard offered sample products/modules, prefer keeping them enabled.

---

# Point 1 — Product Catalog Maintenance (Back Office)

## Goal
Demonstrate that admins can:
- Create products (registration)
- Edit products (modification)
- Disable/delete products (cancellation)
- Consult product information (queries)
And answer:
- How products are grouped by category + what “main category” is
- At least **3 stock management actions** preventing sale of unavailable products

## Codex Tasks

### 1.1 Categories + “Main category” proof
- Create multiple categories and assign products to multiple categories where possible.
- Ensure the product has a clearly selected **Main category** (sometimes called “Default category” in UI wording).
- Document:
  - How to assign multiple categories to one product
  - How to set the main/default category
  - Why main category matters (breadcrumb, canonical category, listing context, etc.)

### 1.2 Stock management: implement 3 actions
Codex must configure and document at least **three** of these (choose those available in the installed PrestaShop 8 UI):

- **Action A:** Set stock quantity to 0 and set product availability behavior to prevent purchase (disable “Add to cart” / mark out of stock).
- **Action B:** Configure “When out of stock” behavior (deny orders vs allow orders) appropriately.
- **Action C:** Disable product (or unpublish) when unavailable.
- **Action D:** Use stock locations/attributes (if variants exist) to keep accurate availability per combination.
- **Action E:** Configure low-stock alerts/thresholds (if present) to help admins keep stock updated.

> Codex must identify where these settings live in Back Office for PrestaShop 8 and write exact navigation paths in `docs/config_checklist.md`.

### 1.3 Evidence required
Codex must define screenshot needs in the checklist:
- Product edit page showing:
  - Categories selection + Main/Default category
  - Stock settings (quantity and out-of-stock behavior)
- Product list showing disable/unpublish or stock status (as applicable)

---

# Point 2 — Product Catalog Queries (Front Office)

## Goal
Ensure users can:
- Browse product lists with **pagination**
- See key characteristics + small image
- Click product to see a detailed page with large image and “Add to cart”
And answer:
- Which **default modules** enable **Ajax live search / autocomplete**
- UX advantages of live search

## Codex Tasks

### 2.1 Pagination + product list display
- Confirm category listing pages show pagination.
- Ensure product tiles show at least:
  - image thumbnail
  - name
  - price
  - link to product detail page
- Document where pagination settings are configured (theme settings / product per page settings, etc.)

### 2.2 Live search / autocomplete using default modules
Codex must:
- Identify which **installed-by-default** modules in PrestaShop 8 Back Office provide:
  - search block
  - live search / autocomplete (Ajax)
- Enable/configure them if disabled.
- Document exact module names as shown in the Modules catalog, and how to configure.

> IMPORTANT: Do not install third-party modules. Only default modules shipped with PrestaShop installation.

### 2.3 UX advantages (writeup guidance)
Codex must add to `docs/config_checklist.md` a short bullet list of UX advantages:
- faster discovery, fewer page loads, reduced friction, typo tolerance, higher conversion, etc.
Keep it practical and aligned to the shop behavior.

### 2.4 Evidence required
Checklist must request screenshots:
- Front Office category page showing pagination + product grid/list
- Front Office search bar showing autocomplete/live results (if enabled)
- Product detail page showing big image + Add to cart

---

# Point 3 — Order Management & Purchase Process

## Goal
Prove a user can:
- Add to cart
- Remove item from cart
- Change quantities and recalc totals
- Proceed to checkout, enter shipping details, select payment method, and place order
Then prove admin can:
- View orders
- View invoices generated
And answer:
- How to consult invoices in bulk
- How to automate order statuses + benefits

## Codex Tasks

### 3.1 Ensure cart behaviors are enabled
Codex must validate that the cart allows:
- Remove item
- Update quantity
- Totals recalculation

If the theme/cart behavior hides these controls, enable them via configuration (not custom code).

### 3.2 Ensure checkout is functional
- Confirm at least one carrier exists and is enabled.
- Confirm at least one payment method exists (built-in/offline like “Pay by check” or “Bank wire” is fine).
- Create a **test customer** (document credentials in `docs/config_checklist.md` but DO NOT commit real personal data; use placeholder email like `test_uoc@example.com`).

### 3.3 Orders + invoices visibility (Back Office)
Codex must document:
- Where orders are listed
- How to open an order and see details
- Where invoices are and how to download/view

### 3.4 “Invoices in bulk” answer coverage
Codex must identify the built-in way(s) to consult or download invoices in bulk (common options include invoice filters by date range, bulk PDF download, order/invoice list actions).  
Write the exact navigation path and the UI elements used.

### 3.5 Order status automation + benefits
Codex must document:
- Where order statuses live
- How PrestaShop updates statuses based on payment modules and order workflow
- Benefits: faster operations, fewer manual errors, better customer comms, consistent accounting, etc.

> Note: This is largely explanatory and configuration-based; no custom automation engine should be added.

### 3.6 Evidence required
Checklist must request screenshots:
- Cart page showing remove item + quantity update
- Checkout steps showing shipping + payment selection
- Back Office order detail view
- Back Office invoices page / bulk invoice download UI
- Back Office order statuses configuration page (or equivalent)

---

# Point 4 — Payment Systems (PayPal — Theoretical)

## Goal
Investigate PayPal module for PrestaShop and document:
- Basic installation process (in PrestaShop 8)
- Required PayPal API credentials
- Surcharge option and purpose
No real installation required.

## Codex Tasks

### 4.1 Create `docs/paypal_analysis.md`
Codex must write a concise document describing:
- How to find/install the official PayPal module from the Modules catalog in PrestaShop
- Typical PayPal credential types used in such integrations:
  - Client ID / Secret (REST API)
  - Live vs Sandbox environment
  - Webhook ID / webhook configuration (if described as needed)
  - Merchant account / email linkage (as applicable)
- What “surcharge” means in context:
  - adding a fee for using PayPal
  - why merchants use it (cost recovery) and where it might be configured

> Do not invent exact field names unless confirmed in the module UI you can see locally. If unknown, phrase as “commonly required” credential types.

### 4.2 Evidence required
Since real installation is not required:
- Add guidance in `docs/config_checklist.md` for screenshots of:
  - Modules page showing PayPal module listing (if visible)
  - Any info pages used (optional)

---

## Implementation Notes (How to Work in This Repo)

### A) Configuration-first workflow
1. Inspect Modules > Module Manager and list installed default modules
2. Enable/Configure only what is required
3. Create minimal data (categories/products) for screenshots
4. Place one test order

### B) Optional Helper Module: `uoc_practice2`
If created, it must:
- Add a Back Office menu entry “UOC Practice 2”
- Show:
  - Links to: Categories, Products, Orders, Invoices, Order Statuses, Modules
  - A “coverage checklist” table with YES/NO toggles (informational only)
  - Current key settings (read-only) if easy to fetch:
    - products per page
    - out of stock behavior
    - enabled search modules

NO overrides, NO front office hooks that change behavior.

---

## Repo Hygiene (Required)

- Add/extend `.gitignore` so local runtime files do not get committed:
  - `/var/`
  - `/cache/`
  - `/log/`
  - `/config/settings.inc.php` (or any DB credential file)
- Do not commit personal data; use dummy test accounts.

---

## Output Files Summary (Codex must create)

- `docs/config_checklist.md`
- `docs/paypal_analysis.md`
- (Optional) `modules/uoc_practice2/` (minimal module)
- `.gitignore` updates as needed

---

## Acceptance Criteria

This repo is “done” when:
- A PrestaShop 8 install can be configured to demonstrate points 1–3 via UI
- Documentation in `docs/` clearly states where to click + what screenshots to take
- PayPal analysis doc covers the requested points without requiring real credentials
- No core hacks, no unnecessary modules, no overengineering
