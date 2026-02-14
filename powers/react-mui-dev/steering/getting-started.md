# Getting Started with React + Material-UI Development

This guide helps you quickly start building React applications with Material-UI.

## Quick Start

### 1. Project Setup

For new projects:
```bash
npx create-react-app my-app
cd my-app
npm install @mui/material @emotion/react @emotion/styled
npm install @mui/icons-material  # Optional: for icons
```

For existing projects:
```bash
npm install @mui/material @emotion/react @emotion/styled
```

### 2. Basic App Structure

```jsx
import { ThemeProvider, createTheme } from '@mui/material/styles';
import CssBaseline from '@mui/material/CssBaseline';
import { Container } from '@mui/material';

const theme = createTheme();

function App() {
  return (
    <ThemeProvider theme={theme}>
      <CssBaseline />
      <Container>
        {/* Your components */}
      </Container>
    </ThemeProvider>
  );
}

export default App;
```

## Common Components

### Buttons
```jsx
import { Button, IconButton } from '@mui/material';
import DeleteIcon from '@mui/icons-material/Delete';

<Button variant="contained">Contained</Button>
<Button variant="outlined">Outlined</Button>
<Button variant="text">Text</Button>
<IconButton><DeleteIcon /></IconButton>
```

### Layout
```jsx
import { Grid, Box, Stack } from '@mui/material';

<Grid container spacing={2}>
  <Grid item xs={12} md={6}>Content</Grid>
  <Grid item xs={12} md={6}>Content</Grid>
</Grid>

<Stack direction="row" spacing={2}>
  <Box>Item 1</Box>
  <Box>Item 2</Box>
</Stack>
```

### Forms
```jsx
import { TextField, Select, MenuItem, Checkbox } from '@mui/material';

<TextField label="Name" variant="outlined" fullWidth />
<Select value={value} onChange={handleChange}>
  <MenuItem value={1}>Option 1</MenuItem>
  <MenuItem value={2}>Option 2</MenuItem>
</Select>
```

## Styling Approaches

### 1. sx Prop (Recommended)
```jsx
<Box sx={{ 
  p: 2, 
  bgcolor: 'primary.main', 
  color: 'white',
  '&:hover': { bgcolor: 'primary.dark' }
}}>
  Content
</Box>
```

### 2. Styled Components
```jsx
import { styled } from '@mui/material/styles';

const StyledBox = styled(Box)(({ theme }) => ({
  padding: theme.spacing(2),
  backgroundColor: theme.palette.primary.main,
}));
```

## Responsive Design

```jsx
<Box sx={{
  width: { xs: '100%', sm: '50%', md: '33%' },
  display: { xs: 'block', md: 'flex' }
}}>
  Responsive content
</Box>
```

## Next Steps

1. Explore MUI component documentation via the MUI MCP
2. Customize your theme
3. Build reusable component patterns
4. Add form validation
5. Implement responsive layouts
