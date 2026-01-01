# 🛒 PrestaShop 8 – Minimal Academic MVP

## Context (IMPORTANT)

This repository contains a **standard PrestaShop 8 installation**.

DO NOT generate a shop from scratch.  
DO NOT replace PrestaShop core files.

All functionality must rely on:
- PrestaShop core features
- PrestaShop Back Office configuration
- Optional **very small custom module**, only if strictly necessary

The goal is to demonstrate **basic e-commerce operations**, not custom development.

---

## Environment

- PrestaShop 8.x
- PHP 8.1
- MySQL
- Apache (XAMPP compatible)
- Local installation

---

## MVP Scope (MINIMUM)

The MVP consists of verifying and minimally configuring the following **core PrestaShop features**:

### 1️⃣ Product Catalog

Using the Back Office:

- Create at least **2 product categories**
- Create at least **3 products**
- Assign each product to **one main category**
- Set:
  - Name
  - Description
  - Price
  - Stock quantity

Ensure:
- Products with stock = 0 cannot be purchased

NO custom code required.

---

### 2️⃣ Product Listing & Search

Using PrestaShop defaults:

- Product listing page shows:
  - Product name
  - Price
  - Image
- Pagination is enabled
- Product detail page exists

Enable and use:
- Default PrestaShop search
- Live search / autocomplete if available via default modules

NO custom code required.

---

### 3️⃣ Cart & Order Process

Using PrestaShop core checkout:

- User can:
  - Add product to cart
  - Remove product from cart
  - Change quantity
- Prices update automatically

Complete a test purchase using:
- A test user account
- Default checkout flow

Ensure:
- Order is visible in Back Office
- Invoice is generated

NO custom code required.

---

### 4️⃣ Payment (Simulated)

- Use **PrestaShop default payment options**
- Do NOT configure real PayPal credentials
- Payment analysis is **theoretical only**

NO custom code required.

---

## Optional Code (ONLY IF NEEDED)

If any requirement cannot be demonstrated with configuration alone:

- Create **one minimal module** under:
  `/modules/mvpinfo/`

The module may:
- Add a comment
- Expose configuration info
- Add a simple admin message

The module must:
- Contain minimal PHP
- Not override core behavior
- Be clearly documented

---

## What Codex SHOULD Do

- Identify which requirements are met by configuration
- Identify where screenshots are required
- (If requested) generate:
  - A minimal custom module skeleton
  - README notes explaining where to click in Back Office

---

## What Codex MUST NOT Do

- Do NOT rewrite PrestaShop
- Do NOT add themes
- Do NOT add external modules
- Do NOT invent features
- Do NOT implement custom checkout or payments

PrestaShop is the product.

---

## Guiding Principle

If PrestaShop already does it, **use it**.  
If configuration is enough, **do not code**.  
If coding is unavoidable, **write the smallest possible module**.

