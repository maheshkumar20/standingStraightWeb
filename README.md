# Standing Straight - Monorepo

A modern, responsive website for Standing Straight, a non-profit organization dedicated to providing life-changing spinal surgeries to children in underserved communities.

## About Standing Straight

Standing Straight delivers free spinal correction surgeries and trains local medical teams to create lasting impact in underserved communities. Our mission is to ensure every child has the chance to stand tall and live with dignity.

## Monorepo Structure

This project is organized as a monorepo containing:

```
standing-straight/
├── studio/                    # Sanity Studio (CMS)
│   ├── sanity.config.ts      # Sanity configuration
│   ├── package.json          # Studio dependencies
│   ├── schemaTypes/          # Content schemas
│   └── docs/                 # Studio documentation
├── web/                      # React website
│   ├── src/                  # Source code
│   ├── public/               # Static assets
│   ├── package.json          # Web dependencies
│   └── vite.config.ts        # Vite configuration
├── package.json              # Root workspace configuration
└── README.md                 # This file
```

## Technology Stack

### Studio (CMS)

- **Sanity Studio**: Headless CMS for content management
- **React**: UI framework for the studio interface
- **TypeScript**: Type-safe development

### Web Application

- **Frontend Framework**: React 18 with TypeScript
- **Build Tool**: Vite for fast development and optimized builds
- **Styling**: Tailwind CSS with custom design system
- **UI Components**: shadcn/ui component library
- **Routing**: React Router for seamless navigation
- **Icons**: Lucide React for consistent iconography
- **Animations**: CSS transitions and transforms
- **Content**: Sanity Client for CMS integration

## Getting Started

### Prerequisites

- Node.js (v16 or higher)
- npm (v8 or higher)

### Installation

1. **Clone the repository**

   ```bash
   git clone <repository-url>
   cd standing-straight
   ```

2. **Install all dependencies**

   ```bash
   npm install
   ```

   This will install dependencies for the root workspace and both packages.

3. **Set up environment variables**

   **For the web application:**

   ```bash
   cp web/env.example web/.env
   # Edit web/.env with your Sanity project details
   ```

   **For the studio:**

   ```bash
   cp studio/env.example studio/.env
   # Edit studio/.env with your Sanity project details
   ```

### Development

#### Start both applications

```bash
npm run dev:all
```

#### Start individual applications

```bash
# Start web application only (http://localhost:5173)
npm run dev

# Start Sanity Studio only (http://localhost:3333)
npm run dev:studio
```

#### Other useful commands

```bash
# Build for production
npm run build:all

# Lint code
npm run lint:all

# Preview production build
npm run preview

# Clean all node_modules
npm run clean
```

## Project Structure

### Web Application (`/web`)

```
web/
├── src/
│   ├── components/           # Reusable UI components
│   │   ├── cms/             # CMS-connected components
│   │   ├── direct/          # Direct/static components
│   │   ├── shared/          # Shared components
│   │   └── ui/              # shadcn/ui components
│   ├── hooks/               # Custom React hooks
│   ├── lib/                 # Utility functions
│   │   ├── sanity.ts        # Sanity client configuration
│   │   └── utils.ts         # General utilities
│   ├── pages/               # Page components
│   └── assets/              # Static assets
├── public/                  # Public static files
└── package.json
```

### Studio (`/studio`)

```
studio/
├── schemaTypes/             # Sanity schema definitions
│   ├── contactInfo.ts
│   ├── event.ts
│   ├── heroSection.ts
│   ├── mission.ts
│   └── ...
├── docs/                    # Documentation
├── sanity.config.ts         # Studio configuration
└── package.json
```

## Key Features

### Content Management

- **Sanity Studio**: Intuitive CMS for content editors
- **Real-time Preview**: See changes instantly
- **Media Management**: Optimized image handling
- **Structured Content**: Type-safe content schemas

### Web Application

- **Responsive Design**: Mobile-first approach
- **Modern UI/UX**: Clean, professional design
- **Interactive Components**: Enhanced hover effects and transitions
- **Accessibility**: WCAG compliant design patterns
- **Performance**: Optimized builds and lazy loading

## Development Workflow

### Adding New Content Types

1. **Create schema in studio:**

   ```bash
   # Add new schema file in studio/schemaTypes/
   touch studio/schemaTypes/newContentType.ts
   ```

2. **Export schema:**

   ```typescript
   // studio/schemaTypes/index.ts
   export { default as newContentType } from "./newContentType";
   ```

3. **Add TypeScript interface:**

   ```typescript
   // web/src/lib/sanity.ts
   export interface NewContentType {
     // Define interface
   }
   ```

4. **Create query functions:**
   ```typescript
   // web/src/lib/sanity.ts
   export async function getNewContentTypes() {
     // Implement query
   }
   ```

### Workspace Commands

All commands support workspace-specific execution:

```bash
# Run command in specific workspace
npm run <command> --workspace=web
npm run <command> --workspace=studio

# Examples
npm run build --workspace=web
npm run dev --workspace=studio
npm install <package> --workspace=web
```

## Environment Variables

### Web Application (`web/.env`)

```
VITE_SANITY_PROJECT_ID=your_project_id
VITE_SANITY_DATASET=production
```

### Studio (`studio/.env`)

```
SANITY_STUDIO_PROJECT_ID=your_project_id
SANITY_STUDIO_DATASET=production
```

## Deployment

### Web Application

```bash
npm run build
# Deploy web/dist directory to your hosting platform
```

### Sanity Studio

```bash
npm run build:studio
npm run deploy --workspace=studio
```

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## Scripts Reference

| Command                | Description                  |
| ---------------------- | ---------------------------- |
| `npm run dev`          | Start web development server |
| `npm run dev:studio`   | Start Sanity Studio          |
| `npm run dev:all`      | Start both applications      |
| `npm run build`        | Build web application        |
| `npm run build:studio` | Build Sanity Studio          |
| `npm run build:all`    | Build both applications      |
| `npm run lint`         | Lint web application         |
| `npm run lint:studio`  | Lint studio                  |
| `npm run lint:all`     | Lint both applications       |
| `npm run preview`      | Preview web production build |
| `npm run clean`        | Clean all node_modules       |

---

**Standing Straight - Together We Stand**
