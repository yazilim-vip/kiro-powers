---
name: react-mui-dev
displayName: React + Material-UI Development
description: Build modern React applications with Material-UI components using the official MUI MCP server
keywords: [react, mui, material-ui, components, theming, responsive design, ui development]
version: 1.0.0
license: MIT
---

# React + Material-UI Development Power

Build modern React applications with Material-UI components and best practices.

## What is React + MUI Development?

This power helps you develop React applications using Material-UI (MUI), Google's Material Design implementation for React. It includes the official MUI MCP server for real-time component documentation, examples, and guidance.

## Features

- Official MUI MCP server integration (`@mui/mcp`)
- Component API documentation and examples
- Material Design principles and patterns
- Responsive design with Grid and breakpoints
- Theme customization and styling guidance
- Form handling with MUI components
- Accessibility best practices
- Icon integration with `@mui/icons-material`

## Usage

Ask Kiro for help with React and MUI development:

```
"Show me how to use MUI Button with variants"
"Create a responsive MUI Card layout"
"How do I customize the MUI theme colors?"
"Create a form with MUI TextField and validation"
```

Kiro will provide component examples, theming guidance, and best practices using the MUI MCP server.

## Quick Start

### Installation

```bash
npm install @mui/material @emotion/react @emotion/styled
npm install @mui/icons-material  # Optional: for icons
```

### Basic Setup

```jsx
import { ThemeProvider, createTheme } from '@mui/material/styles';
import CssBaseline from '@mui/material/CssBaseline';

const theme = createTheme();

function App() {
  return (
    <ThemeProvider theme={theme}>
      <CssBaseline />
      {/* Your components */}
    </ThemeProvider>
  );
}
```

## Common Patterns

### Component Structure
```jsx
import { Button, Card, CardContent } from '@mui/material';

function MyComponent() {
  return (
    <Card>
      <CardContent>
        <Button variant="contained" color="primary">
          Click Me
        </Button>
      </CardContent>
    </Card>
  );
}
```

### Theming
```jsx
import { createTheme, ThemeProvider } from '@mui/material/styles';

const theme = createTheme({
  palette: {
    primary: { main: '#1976d2' },
    secondary: { main: '#dc004e' },
  },
});

function App() {
  return (
    <ThemeProvider theme={theme}>
      {/* Your app */}
    </ThemeProvider>
  );
}
```

## When to Use This Power

- Starting a new React + MUI project
- Adding MUI components to existing React apps
- Customizing MUI themes and styles
- Building responsive, accessible interfaces
- Learning MUI best practices and patterns

## Tips

- Always check component props and variants via the MUI MCP
- Use TypeScript for better type safety with MUI
- Leverage MUI's built-in responsive utilities
- Test components across different screen sizes
- Follow MUI's composition patterns for complex UIs
