# React + Material-UI Development Power

A comprehensive power for building modern React applications with Material-UI (MUI) components, leveraging the official MUI MCP server for component guidance and best practices.

## What This Power Does

This power helps you:
- Build React applications with Material-UI components
- Get real-time MUI component documentation and examples
- Follow Material Design principles and MUI best practices
- Create responsive, accessible UI components
- Integrate MUI theming and styling solutions

## MCP Server Integration

This power includes the official MUI MCP server (`@mui/mcp`) which provides:
- Component API documentation
- Usage examples and patterns
- Theming guidance
- Accessibility best practices
- Migration guides

## Key Capabilities

- React component development with hooks and modern patterns
- Material-UI component integration and customization
- Responsive design with MUI Grid and breakpoints
- Theme customization and styling with `sx` prop and styled components
- Form handling with MUI form components
- Accessibility-compliant UI development

## Getting Started

1. Ask about MUI components: "Show me how to use MUI Button with variants"
2. Request component examples: "Create a responsive MUI Card layout"
3. Get theming help: "How do I customize the MUI theme colors?"
4. Build forms: "Create a form with MUI TextField and validation"

## Best Practices

- Use MUI's `sx` prop for component-level styling
- Leverage the theme system for consistent design
- Follow Material Design guidelines
- Ensure responsive layouts with Grid and breakpoints
- Maintain accessibility with proper ARIA attributes
- Use MUI icons from `@mui/icons-material`

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
