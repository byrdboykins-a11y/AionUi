# AionUi Project Structure

## Directory Overview

```
AionUi/
├── .github/
│   └── workflows/           # GitHub Actions CI/CD workflows
│       └── ci.yml          # Continuous integration pipeline
│
├── src/
│   ├── components/          # Reusable React components
│   │   ├── common/         # Shared components (Button, Modal, etc.)
│   │   ├── layout/         # Layout components (Header, Sidebar, etc.)
│   │   └── features/       # Feature-specific components
│   │
│   ├── pages/              # Page-level components (routed)
│   │   ├── Home.tsx
│   │   ├── Dashboard.tsx
│   │   └── Settings.tsx
│   │
│   ├── services/           # External service integrations
│   │   ├── gemini.ts       # Gemini API service
│   │   ├── claude.ts       # Claude API service
│   │   ├── openai.ts       # OpenAI API service
│   │   ├── qwen.ts         # Qwen API service
│   │   └── api.ts          # General API utilities
│   │
│   ├── hooks/              # Custom React hooks
│   │   ├── useAuth.ts
│   │   ├── useApi.ts
│   │   └── useDarkMode.ts
│   │
│   ├── types/              # TypeScript type definitions
│   │   ├── index.ts        # Exported types
│   │   ├── api.ts          # API response types
│   │   ├── models.ts       # Data model types
│   │   └── common.ts       # Common types
│   │
│   ├── utils/              # Utility functions
│   │   ├── constants.ts    # Application constants
│   │   ├── helpers.ts      # Helper functions
│   │   ├── validators.ts   # Form/data validation
│   │   └── formatters.ts   # Data formatting utilities
│   │
│   ├── styles/             # Global styles
│   │   ├── index.css       # Global CSS
│   │   ├── variables.css   # CSS variables
│   │   └── themes.css      # Theme definitions
│   │
│   ├── App.tsx             # Main application component
│   ├── main.tsx            # Application entry point
│   └── vite-env.d.ts       # Vite environment types
│
├── public/                 # Static assets (images, fonts, etc.)
│   └── favicon.ico
│
├── dist/                   # Production build output (generated)
│
├── .env.example            # Environment variables template
├── .gitignore              # Git ignore rules
├── package.json            # Project dependencies and scripts
├── package-lock.json       # Locked dependency versions
├── tsconfig.json           # TypeScript configuration
├── vite.config.ts          # Vite build configuration
├── SETUP.md                # Setup guide
├── CONTRIBUTING.md         # Contribution guidelines
├── PROJECT_STRUCTURE.md    # This file
└── README.md               # Project overview
```

## File Naming Conventions

### Components
- **PascalCase** for files: `UserProfile.tsx`, `Dashboard.tsx`
- **Index exports**: Each component folder should have `index.ts` or `index.tsx`

### Utilities & Services
- **camelCase** for files: `apiService.ts`, `formatter.ts`

### Types & Interfaces
- **camelCase** for files: `apiTypes.ts`, `models.ts`
- **PascalCase** for exported types: `type User = { ... }`

### Styles
- **kebab-case** for class names: `.component-name`, `.button-primary`
- Co-locate CSS with components when possible

## Key Directories Explained

### `/src/components`
Reusable UI components that can be used across multiple pages.
- **common/**: Generic, reusable components (buttons, modals, etc.)
- **layout/**: Layout wrapper components (header, sidebar, footer)
- **features/**: Domain-specific components (AI platform selectors, settings)

### `/src/services`
Handles all external API communication.
- Abstracts API logic from React components
- Manages authentication and API calls
- Handles error responses and retries

### `/src/hooks`
Custom React hooks for shared stateful logic.
- Follows React conventions (useXyz naming)
- Can use other hooks internally
- Should be pure and reusable

### `/src/types`
Central location for all TypeScript type definitions.
- Reduces circular imports
- Makes types discoverable
- Organized by domain (api.ts, models.ts, etc.)

### `/src/utils`
Pure functions and constants.
- No side effects
- No external dependencies (except types)
- Highly testable

### `/src/styles`
Global styling and CSS variables.
- CSS custom properties for theming
- Global resets and base styles
- Shared animations and transitions

## Import Path Aliases

Configure in `tsconfig.json` for cleaner imports:
```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["src/*"],
      "@components/*": ["src/components/*"],
      "@services/*": ["src/services/*"],
      "@types/*": ["src/types/*"],
      "@utils/*": ["src/utils/*"],
      "@hooks/*": ["src/hooks/*"]
    }
  }
}
```

Usage:
```typescript
// Instead of
import { UserProfile } from '../../../components/UserProfile'
import { apiService } from '../../../services/api'

// Use
import { UserProfile } from '@components/UserProfile'
import { apiService } from '@services/api'
```

## Adding New Features

1. **Create component** in `src/components/features/YourFeature/`
2. **Add types** to `src/types/yourFeature.ts`
3. **Create service** in `src/services/yourFeature.ts` if needed
4. **Add utilities** to `src/utils/` as needed
5. **Add tests** alongside your code
6. **Update** `src/components/index.ts` for exports

## Best Practices

- Keep components focused and small
- Extract reusable logic into hooks and utilities
- Centralize type definitions
- Use services for all API calls
- Add comments for complex logic
- Follow established naming conventions
- Test edge cases
- Keep styles scoped and organized
