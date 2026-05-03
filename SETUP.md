# AionUi Setup Guide

Welcome to **AionUi** - A free, local, open-source 24/7 Cowork app with support for multiple AI platforms!

## 📋 Prerequisites

- **Node.js**: v18.x or v20.x (recommended: v20.x)
- **npm**: v9.x or higher (or yarn/pnpm alternative)
- **Git**: Latest version

## 🚀 Installation

### 1. Clone the Repository
```bash
git clone https://github.com/byrdboykins-a11y/AionUi.git
cd AionUi
```

### 2. Install Dependencies
```bash
npm install
# or
yarn install
# or
pnpm install
```

### 3. Environment Setup
```bash
# Copy the example env file
cp .env.example .env.local

# Edit .env.local with your API keys
nano .env.local  # or use your favorite editor
```

### 4. Start Development Server
```bash
npm run dev
# The app will typically be available at http://localhost:5173
```

## 🏗️ Project Structure

```
AionUi/
├── src/
│   ├── components/      # React components
│   ├── pages/          # Page components
│   ├── services/       # API and external service integrations
│   ├── hooks/          # Custom React hooks
│   ├── types/          # TypeScript type definitions
│   ├── utils/          # Utility functions
│   ├── styles/         # Global CSS styles
│   └── App.tsx         # Main app component
├── public/             # Static assets
├── dist/               # Production build output
├── .github/workflows/  # CI/CD configurations
├── package.json        # Project dependencies
├── tsconfig.json       # TypeScript configuration
└── vite.config.ts      # Vite configuration
```

## 📦 Available Scripts

```bash
# Development
npm run dev              # Start dev server

# Building
npm run build            # Build for production
npm run preview          # Preview production build

# Code Quality
npm run lint             # Run ESLint
npm run type-check       # Run TypeScript type checker
npm run format           # Format code with Prettier

# Testing
npm run test             # Run unit tests
npm test -- --coverage  # Generate coverage report
```

## 🔑 Supported AI Platforms

- **Gemini** - Google's AI model
- **Claude** - Anthropic's AI assistant
- **OpenAI** - GPT models
- **Qwen** - Alibaba's AI model
- **Goose CLI** - Code automation tool
- **Auggie** - AI enhancement platform
- **CodeX** - Code understanding tool
- **OpenCode** - Open-source code platform

## ⚙️ Configuration

### API Keys
Add your API keys to `.env.local`:
```
VITE_GEMINI_API_KEY=your_key_here
VITE_CLAUDE_API_KEY=your_key_here
VITE_OPENAI_API_KEY=your_key_here
```

### Feature Flags
Enable/disable features in `.env.local`:
```
VITE_ENABLE_GEMINI=true
VITE_ENABLE_CLAUDE=true
VITE_ENABLE_OPENAI=true
```

## 🐛 Troubleshooting

### Port Already in Use
```bash
# Use a different port
npm run dev -- --port 3000
```

### Dependency Issues
```bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install
```

### TypeScript Errors
```bash
# Run type checker
npm run type-check
```

## 📚 Additional Resources

- [Vite Documentation](https://vitejs.dev/)
- [React Documentation](https://react.dev/)
- [TypeScript Documentation](https://www.typescriptlang.org/)

## 🤝 Need Help?

See [CONTRIBUTING.md](./CONTRIBUTING.md) for contribution guidelines and support information.

## ⭐ Show Your Support

If you find AionUi helpful, please consider starring the repository!
