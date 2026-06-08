# App

This folder will contain the source code for the Garimpa AI web application.

In the initial phase, the app will be prototyped with Lovable using mocked data. Once the prototype is validated, the application may be connected to Supabase and later integrated with AI and official marketplace APIs.

## Planned responsibilities

The app should include:

- public landing page;
- product suggestion dashboard;
- product search and filters;
- product details screen;
- marketplace comparison screen;
- AI-powered ad generator;
- saved products;
- admin area for manual product and offer registration;
- privacy and terms pages.

## Development principles

The application should follow:

- clean code;
- reusable components;
- clear naming conventions;
- separation of responsibilities;
- form validation;
- secure environment variable usage;
- no secrets exposed in the frontend;
- LGPD-aware data handling;
- no unauthorized scraping;
- preparation for future Supabase integration.

## Future structure

The source code may later be organized into folders such as:

```text
src/
├── components/
├── pages/
├── hooks/
├── services/
├── lib/
├── types/
└── utils/