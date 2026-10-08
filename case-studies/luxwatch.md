# LuxWatch

**Category:** Marketplace / SaaS Product  
**Source code:** Private  
**Role:** Product Engineer with end-to-end ownership of the marketplace architecture, buyer/seller workflows, data model, listing lifecycle, discovery, seller tooling, and responsive UX.  
**Problem:** A luxury watch marketplace needs two journeys in one product: buyers discovering and contacting sellers, and sellers creating and managing their own listings.  
**Result:** A two-sided marketplace with buyer-facing browse, search, and product pages and a seller dashboard for creating and editing listings, responsive on desktop and mobile.  

## Overview

LuxWatch is a two-sided luxury watch marketplace: buyers discover and compare listings, and sellers create and manage their own.

It is a marketplace, not a product gallery. Buyers browse, search, and filter a catalog and contact sellers from a product page, while sellers work in their own area to create, edit, and publish listings with images. I owned the product end to end, from the architecture and data model to the buyer and seller flows, backend logic, and responsive UX.

- Buyer journey: landing page, featured watches, browse with search and filters, and product pages
- Seller journey: a products dashboard with create, edit, publish status, and delete
- Listing model: brand, model, year, condition, price, category, description, and up to eight images
- Responsive layout: the same marketplace pages on desktop and mobile

![Browse Collection: search, filters, and sorting over the watch catalog](../assets/luxwatch/cover/browse-collection.webp)
![The marketplace system at a glance: the seller's product dashboard behind the buyer's Browse Collection](../assets/luxwatch/screenshots/overview.png)

## Product outcomes & evidence

No numeric results are claimed. The evidence is the shipped product itself, as shown in its own screens.

- Landing and discovery: a landing page with Explore Collection and Start Selling entry points, and a featured watches carousel.
- Browse, search, and filters: search, category, brand, condition, and price range filters, with sorting such as Newest First.
- Product detail: brand, title, model, price, condition, year, seller, description, a Contact Seller action, and related watches.
- Seller product management: a My Products list with price, status, created date, and edit and delete actions, plus Create Product.
- Create and edit listing: title, brand, model, description, year, condition, price, and category, with image management.
- Responsive experience: the featured carousel and product pages on mobile.

![Product detail: the buyer's view of a listing, with a Contact Seller action](../assets/luxwatch/screenshots/product-detail.webp)
![My Products: the seller's view of the same listings, with status and actions](../assets/luxwatch/screenshots/seller-dashboard.webp)

## Key product & engineering decisions

- Buyer and seller journeys kept separate: buyers use the public landing, browse, and product pages, while sellers use their own account area with Profile, Products, Messages, and Settings.
- Catalog, search, and filters: browse combines text search with category, brand, condition, and price-range filters and a sort order, so buyers can narrow the catalog by what matters to them.
- Listing lifecycle and status: each listing has a status and a created date, and can be edited or deleted from one list.
- Product image management: a listing holds up to eight images, with a default image, and images are added from the edit form.
- Responsive marketplace UX: the same marketplace pages adapt to mobile, from the featured carousel to the product page.

![Edit Product: listing details, pricing, category, and image management](../assets/luxwatch/screenshots/edit-listing.webp)

## System & architecture

`Next.js` `TypeScript` `Supabase` `PostgreSQL` `Auth / RLS` `Vercel`

I owned the architecture end to end. It is organized like this, based on the product's own navigation and screens:

- Application layer: Next.js and TypeScript, covering the buyer and seller flows and the backend and data logic behind them.
- Relational data model: Supabase and PostgreSQL, holding users, listings (brand, model, year, condition, price, category, description, and status), and their images.
- Authentication and access: Supabase Auth for accounts and row-level security (RLS) for access control.
- Buyer and seller roles: buyers use the public pages, and sellers have a profile and their own product area, with the seller shown on each listing, a Contact Seller action on each product page, and a Messages area for sellers.
- Catalog and listings: published listings with a status and a created date, shown in the browse catalog and on product pages.
- Search and filtering: search, category, brand, condition, and price range, plus sorting.
- Seller management: a products list with create, edit, and delete actions, and one form for creating and editing a listing.
- Media and image workflows: up to eight images per listing, with a default image, added from the edit form.
- Responsive frontend: layouts for desktop and mobile.
- Deployment: Vercel.

![Responsive marketplace: the featured watches and a product page on mobile](../assets/luxwatch/screenshots/mobile.png)

## Validation & production quality

- Create and edit flows: listings are created and edited through one form with basic information, details, pricing, and images.
- Search and filtering: the catalog narrows by search, category, brand, condition, and price range, and shows how many watches match.
- Listing data: the same listing data, such as title, brand, price, and condition, appears consistently on the browse cards, the product page, and the seller list.
- Product images: the edit form shows how many of the eight image slots are used and which image is the default.
- Buyer and seller routes: public pages for buyers and a separate account area for sellers.
- Responsive checks: the same pages are shown on desktop and mobile.

## Outcome

LuxWatch shows marketplace product engineering: a buyer-facing catalog with search and filters and a seller-facing listing workflow, designed as one two-sided product.

Capabilities demonstrated:

- Marketplace product engineering, from discovery to listing management
- Two-sided UX with separate buyer and seller journeys
- Catalog and data modeling for listings, status, and images
- Workflow design for creating and editing listings
- Responsive delivery across desktop and mobile

## Public portfolio note

The listings, prices, and seller profile shown in the screenshots are demo data. Source code and internal implementation details are not public.
