# eslint-simple-import-sort

```js
plugins: ['simple-import-sort']
```

### Import order
- External libraries (react, axios, date-fns, etc.)
- Internal shared libraries (@libs/components)
- Absolute paths within the current app ($src/components, $src/hooks)
- Relative imports (./SomeComponent)
- File-style imports (./style.css, ./styles.ts)

```js
overrides: [
  {
    files: ['*.js', '*.jsx', '*.ts', '*.tsx'],
    rules: {
      'simple-import-sort/imports': [
        'error',
        {
          groups: [
            ['^react', '^@?\\w', '^\\p{L}*\\/.*'],           // External libraries
            ['^@.*', '^@.*/.*'],                             // Internal shared libs (@libs/...)
            ['^\\$.*$'],                                     // Absolute imports ($src/...)
            ['^\\.\\.(?!/?$)', '^\\.\\./?$'],                // Parent relative imports
            ['^\\.\\./\\.\\./.+', '^\\.\\./.+', '^\\.\\/.+'],// Sibling relative imports
            ['^./styles$'],                                  // Style imports
          ],
        },
      ],
    },
  },
],
```
