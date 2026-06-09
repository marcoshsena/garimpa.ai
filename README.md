# Garimpa AI

**AI-powered web assistant for affiliate marketers to compare marketplace products and generate ready-to-use promotional content.**

> Project status: **Planning and MVP prototyping**

---

## Overview

Garimpa AI is a web app concept designed to help affiliate marketers, deal curators, and content creators find product opportunities, compare offers across marketplaces, and generate promotional content for channels such as WhatsApp, Instagram, Reels, Stories, and Telegram.

The main goal is to make affiliate product curation more structured, transparent, and less spammy.

---

## Problem

Many beginner affiliate marketers struggle to:

* choose good products to promote;
* compare offers across different marketplaces;
* understand product potential beyond price;
* create natural and trustworthy promotional messages;
* avoid spam-like communication;
* organize product research and content generation.

As a result, many affiliates share random products with weak copy, little analysis, and low trust.

---

## Solution

Garimpa AI aims to centralize product curation in one place.

The app will allow users to:

* browse suggested products;
* search products by name;
* compare offers from different marketplaces;
* evaluate price, rating, social proof, delivery, and estimated commission level;
* identify the best platform to promote a product;
* generate ready-to-use promotional content with AI;
* save products for later;
* manage products and offers through an admin area.

---

## Planned Features for V1

* Public landing page
* Product suggestion dashboard
* Search and category filters
* Product detail page
* Marketplace comparison table
* Opportunity score from 0 to 10
* Estimated commission level: high, medium, low, or not informed
* AI-generated promotional content
* Copy buttons for ads and links
* Saved products
* Manual admin panel for product and offer registration
* Terms of Use and Privacy Policy pages

---

## Initial Marketplaces

The first version is planned to support product comparison between:

* Amazon
* Mercado Livre
* Shopee
* Magalu

In V1, marketplace data will be manually registered or mocked. Automatic integrations will be studied for future versions using official APIs whenever available.

---

## Tech Stack

Planned technologies:

* **Lovable** for the first visual prototype
* **Supabase** for database, authentication, and storage
* **OpenAI API** for AI-generated promotional content
* **GitHub** for version control and documentation

Future possibilities:

* Marketplace APIs
* Payment integration
* User plans and subscriptions
* Analytics dashboard
* Product ranking automation

---

## Product Principles

Garimpa AI follows these principles:

* No unrealistic income promises
* No guaranteed sales claims
* No unauthorized scraping in the MVP
* Human review before publishing
* Clear affiliate disclosure
* LGPD-aware data handling
* Clean and reusable code structure
* Simple, trustworthy, and non-spammy copywriting

---

## MVP Scope

The first version will focus on validating the product experience before adding complex integrations.

### Included in V1

* Mocked or manually registered product data
* Product cards and filters
* Marketplace comparison screen
* Promotional content generator
* Manual admin area
* Privacy and terms pages

### Not included in V1

* Automatic marketplace scraping
* Real-time product ranking
* Exact commission calculation
* Automatic publishing to WhatsApp or Instagram
* Payment system
* Native mobile app

---

## Documentation

Project documentation will be organized under the `docs/` folder:

```text
docs/
├── escopo-v1.md
├── requisitos-funcionais.md
├── requisitos-nao-funcionais.md
├── lgpd-e-privacidade.md
├── modelagem-dados.md
├── roadmap.md
├── decisoes-tecnicas.md
├── validacao-prototipo-local.md
└── plano-migracao-garimpa-ai-hub.md
```

Prompts used for prototyping and AI generation will be stored under the `prompts/` folder.

---

## Roadmap

### Phase 1 — Foundation

* Create GitHub repository
* Define product scope
* Document MVP requirements
* Register privacy and LGPD guidelines
* Create Lovable prototype prompt

### Phase 2 — Visual Prototype

* Build landing page
* Build product dashboard
* Build product details screen
* Build marketplace comparison screen
* Build ad generator screen
* Build admin screens

### Phase 3 — Database

* Connect Supabase
* Create database schema
* Add authentication
* Configure Row Level Security
* Store products, offers, saved products, and generated ads

### Phase 4 — AI Integration

* Connect AI generation API
* Generate promotional texts dynamically
* Store generated ads history
* Create multiple tone and channel variations

### Phase 5 — Marketplace Integrations

* Study official marketplace APIs
* Start with one marketplace integration
* Add product search and ranking logic
* Improve opportunity scoring

---

## Legal and Privacy Notes

Garimpa AI does not promise income, profit, sales, or commissions.

Product prices, availability, delivery conditions, and commission levels may change and must be reviewed by the user before publishing.

The project is designed with LGPD awareness from the MVP stage and aims to collect only the minimum amount of personal data needed for the app to function.

---

## Status

This project is currently in the planning and MVP prototyping stage.

The current focus is to document requirements, define the first version, create the initial Lovable prototype, and validate the core product experience.
