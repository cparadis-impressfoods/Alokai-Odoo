# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

### Core Commands
- `yarn dev` - Start development server with GraphQL codegen
- `yarn build` - Build for production
- `yarn start` - Start production server
- `yarn preview` - Preview production build locally

### Code Quality
- `yarn lint` - Run ESLint
- `yarn lint:fix` - Fix ESLint issues automatically
- `yarn codegen` - Generate GraphQL types from schema

### Testing
- No specific test commands defined in package.json

## Architecture Overview

This is a **Nuxt 3 e-commerce application** built with Vue Storefront 2 architecture and integrates with Odoo ERP as the backend. The application follows a layered architecture pattern with domain-specific modules.

### Key Technologies
- **Nuxt 3** - Full-stack Vue framework
- **Vue Storefront SDK** - E-commerce SDK for API integration
- **Odoo ERP** - Backend system via GraphQL API
- **Tailwind CSS** + **Storefront UI** - Styling and components
- **GraphQL** - API communication with code generation
- **TypeScript** - Type safety throughout

### Layer-Based Architecture
The application uses Nuxt layers for modular organization:

- **`layers/auth/`** - Authentication & user management
- **`layers/cart-redis/`** - Shopping cart functionality
- **`layers/category/`** - Product category pages
- **`layers/checkout/`** - Checkout process
- **`layers/core/`** - Shared components and utilities
- **`layers/home/`** - Homepage
- **`layers/my-account/`** - User account management
- **`layers/orders/`** - Order history
- **`layers/product/`** - Product pages
- **`layers/search-*/`** - Search functionality (Algolia, default, Luigi)
- **`layers/storyblok/`** - CMS integration
- **`layers/wishlist/`** - Wishlist functionality

### API Architecture
- **GraphQL API** at `/graphql/vsf` endpoint from Odoo
- **Server routes** in `server/api/` handle caching and error handling
- **Fragments/Queries/Mutations** in `server/` directory for GraphQL operations
- **Automatic route generation** from Odoo categories and products via `modules/routes-generator`

### Key Configuration
- **Environment variables** for Odoo connection, caching, and storage
- **SWR caching** configured for performance optimization
- **Custom image provider** for optimized Odoo images
- **I18n** support with English as default
- **SEO** configuration with robots.txt and sitemap generation

### Development Patterns
- **Composables** for business logic (`use*` functions)
- **Layers** extend base functionality without modification
- **SDK pattern** for API communication via Vue Storefront SDK
- **GraphQL codegen** generates TypeScript types from schema
- **Caching strategy** with Redis/storage drivers and SWR

### Important Notes
- GraphQL schema at `https://vsf-odoo18.labs.erpgap.com/graphql/vsf`
- Session management with cookies for authentication
- Custom route generation for SEO-friendly URLs
- Multi-environment support (dev, staging, production)
- Odoo modules in `odoo-modules/` directory extend backend functionality