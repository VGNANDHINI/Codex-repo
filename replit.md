# Overview

This is an AI-powered Forest Rights Act (FRA) Management System designed to digitize and manage legacy Forest Rights Act data in India. The platform serves as a comprehensive FRA Atlas with integrated WebGIS capabilities, enabling visualization and management of individual forest rights (IFR), community rights (CR), and community forest resource rights (CFR). The system combines satellite-based asset mapping with a decision support system (DSS) to help optimize Central Sector Scheme (CSS) benefits for FRA patta holders.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture
The client-side is built using React with TypeScript in a modern SPA (Single Page Application) architecture. Key architectural decisions include:

- **Component Library**: Uses shadcn/ui with Radix UI primitives for consistent, accessible UI components
- **Styling**: Tailwind CSS with custom CSS variables for theming and responsive design
- **State Management**: TanStack React Query for server state management and caching
- **Routing**: Wouter for lightweight client-side routing
- **Map Integration**: Leaflet for interactive geographic visualization with OpenStreetMap tiles
- **Charts**: Recharts for data visualization and analytics dashboards

The frontend follows a component-based architecture with clear separation between UI components, business logic, and data fetching layers.

## Backend Architecture
The server-side uses Express.js with TypeScript in an ESM (ES Modules) configuration:

- **API Design**: RESTful API endpoints following resource-based routing patterns
- **File Handling**: Multer middleware for handling document uploads (PDFs, GeoJSON, shapefiles, satellite imagery)
- **Request Logging**: Custom middleware for API request/response logging and performance monitoring
- **Error Handling**: Centralized error handling with proper HTTP status codes

The backend is designed as a stateless API server that serves both the frontend application and handles data operations.

## Data Storage Solutions
The system uses a PostgreSQL database with Drizzle ORM for type-safe database operations:

- **Database**: PostgreSQL with Neon serverless hosting for scalability
- **ORM**: Drizzle ORM with Zod schema validation for type safety
- **Schema Design**: Relational model with tables for villages, claims, documents, schemes, enrollments, and recommendations
- **Migrations**: Drizzle-kit for database schema migrations and versioning

The schema supports geospatial data storage and complex relationships between FRA entities, CSS schemes, and village assets.

## Authentication and Authorization
Currently uses a session-based approach:
- **Session Management**: connect-pg-simple for PostgreSQL-backed session storage
- **Security**: CORS and request validation middleware

## External Service Integrations

### Geospatial Services
- **OpenStreetMap**: Primary map tile provider for base map visualization
- **Satellite Imagery**: Support for GeoTIFF and other satellite data formats for AI-based asset mapping

### AI/ML Components
The system is designed to integrate with AI services for:
- **Document Processing**: OCR and NER for digitizing legacy FRA documents
- **Satellite Analysis**: Computer vision models for detecting agricultural land, forest cover, water bodies, and homesteads
- **Asset Classification**: Machine learning models for land-use classification

### Development Tools
- **Vite**: Modern build tool with HMR for development
- **TypeScript**: Full-stack type safety with shared schema definitions
- **ESBuild**: Fast production bundling for server-side code

The architecture supports both development and production environments with proper asset serving, error handling, and performance optimization.