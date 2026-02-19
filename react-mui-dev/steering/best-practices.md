# React + MUI Best Practices

Guidelines for building maintainable, performant React applications with Material-UI.

## Component Organization

### File Structure
```
src/
├── components/
│   ├── common/          # Reusable UI components
│   ├── layout/          # Layout components
│   └── features/        # Feature-specific components
├── theme/
│   ├── index.js         # Theme configuration
│   └── overrides.js     # Component overrides
└── App.js
```

### Component Pattern
```jsx
import PropTypes from 'prop-types';
import { Box, Typography } from '@mui/material';

function MyComponent({ title, children }) {
  return (
    <Box sx={{ p: 2 }}>
      <Typography variant="h5">{title}</Typography>
      {children}
    </Box>
  );
}

MyComponent.propTypes = {
  title: PropTypes.string.isRequired,
  children: PropTypes.node,
};

export default MyComponent;
```

## Theming Best Practices

### 1. Centralized Theme
```jsx
// theme/index.js
import { createTheme } from '@mui/material/styles';

export const theme = createTheme({
  palette: {
    primary: { main: '#1976d2' },
    secondary: { main: '#dc004e' },
  },
  typography: {
    fontFamily: '"Roboto", "Helvetica", "Arial", sans-serif',
    h1: { fontSize: '2.5rem', fontWeight: 500 },
  },
  spacing: 8, // Base spacing unit
});
```

### 2. Component Overrides
```jsx
// theme/overrides.js
export const componentOverrides = {
  MuiButton: {
    styleOverrides: {
      root: {
        textTransform: 'none', // Disable uppercase
        borderRadius: 8,
      },
    },
  },
};
```

## Performance Optimization

### 1. Lazy Loading
```jsx
import { lazy, Suspense } from 'react';
import { CircularProgress } from '@mui/material';

const HeavyComponent = lazy(() => import('./HeavyComponent'));

function App() {
  return (
    <Suspense fallback={<CircularProgress />}>
      <HeavyComponent />
    </Suspense>
  );
}
```

### 2. Memoization
```jsx
import { memo, useMemo } from 'react';

const ExpensiveComponent = memo(({ data }) => {
  const processedData = useMemo(() => {
    return data.map(item => /* expensive operation */);
  }, [data]);
  
  return <div>{/* render */}</div>;
});
```

## Styling Best Practices

### 1. Use Theme Values
```jsx
// Good
<Box sx={{ p: 2, color: 'primary.main' }} />

// Avoid
<Box sx={{ padding: '16px', color: '#1976d2' }} />
```

### 2. Responsive Design
```jsx
<Box sx={{
  display: 'flex',
  flexDirection: { xs: 'column', md: 'row' },
  gap: { xs: 1, md: 2 },
}}>
```

### 3. Reusable Styles
```jsx
const cardStyles = {
  p: 2,
  borderRadius: 2,
  boxShadow: 1,
  '&:hover': { boxShadow: 3 },
};

<Card sx={cardStyles}>Content</Card>
```

## Accessibility

### 1. Semantic HTML
```jsx
<Button component="a" href="/page">Link Button</Button>
<Typography component="h1" variant="h4">Title</Typography>
```

### 2. ARIA Labels
```jsx
<IconButton aria-label="delete">
  <DeleteIcon />
</IconButton>

<TextField 
  label="Email"
  aria-describedby="email-helper-text"
  helperText="We'll never share your email"
/>
```

### 3. Keyboard Navigation
```jsx
<Button onClick={handleClick} onKeyPress={handleKeyPress}>
  Action
</Button>
```

## Form Handling

### 1. Controlled Components
```jsx
function MyForm() {
  const [values, setValues] = useState({ name: '', email: '' });
  
  const handleChange = (e) => {
    setValues({ ...values, [e.target.name]: e.target.value });
  };
  
  return (
    <form>
      <TextField 
        name="name"
        value={values.name}
        onChange={handleChange}
      />
    </form>
  );
}
```

### 2. Validation
```jsx
const [errors, setErrors] = useState({});

const validate = () => {
  const newErrors = {};
  if (!values.email.includes('@')) {
    newErrors.email = 'Invalid email';
  }
  setErrors(newErrors);
  return Object.keys(newErrors).length === 0;
};

<TextField 
  error={!!errors.email}
  helperText={errors.email}
/>
```

## Common Pitfalls to Avoid

1. Don't mix styling approaches (choose sx prop OR styled components)
2. Don't hardcode colors/spacing (use theme values)
3. Don't forget responsive breakpoints
4. Don't skip accessibility attributes
5. Don't over-customize (leverage MUI defaults)

## Testing

```jsx
import { render, screen } from '@testing-library/react';
import { ThemeProvider, createTheme } from '@mui/material/styles';

const theme = createTheme();

test('renders button', () => {
  render(
    <ThemeProvider theme={theme}>
      <MyComponent />
    </ThemeProvider>
  );
  expect(screen.getByRole('button')).toBeInTheDocument();
});
```
