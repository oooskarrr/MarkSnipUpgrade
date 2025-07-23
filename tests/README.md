# MarkSnip Testing Guide

This guide explains how to set up and run the test suite for the MarkSnip extension. The tests verify the core functionality of converting HTML to Markdown.

## Prerequisites

You'll need:
- Python 3.x (to run a local server)
- A modern web browser (Chrome, Firefox, etc.)
- The MarkSnip source code

## Directory Structure

Ensure your project has the following structure:
```
marksnip/
├── src/
│   ├── background/
│   │   ├── turndown.js
│   │   ├── turndown-plugin-gfm.js
│   │   ├── Readability.js
│   │   └── ...
│   └── ...
└── tests/
    ├── test-runner.html
    ├── test-page.html
    └── README.md
```

## Setting Up the Test Environment

1. **Open Terminal/Command Prompt**
   Navigate to your project root directory (where both `src` and `tests` folders are located):
   ```bash
   cd path/to/marksnip
   ```

2. **Start Local Server**
   Run one of these commands depending on your Python version:
   ```bash
   # For Python 3
   python -m http.server 8000
   
   # For Python 2
   python -m SimpleHTTPServer 8000
   ```
   You should see output like:
   ```
   Serving HTTP on 0.0.0.0 port 8000 (http://0.0.0.0:8000/) ...
   ```

3. **Access the Tests**
   Open your web browser and go to:
   ```
   http://localhost:8000/tests/test-runner.html
   ```

## Running Tests

The tests will run automatically when you load test-runner.html. Results appear on the page showing:
- Green: Test passed
- Red: Test failed (with error details)

### Test Output

The test results show:
- Test name and status
- Expected vs actual output for failed tests
- Detailed error messages when tests fail

Check the browser's console (F12 or right-click -> Inspect -> Console) for additional debugging information.

## Modifying Tests

- `test-page.html`: Contains the HTML input for testing
- `test-runner.html`: Contains the test logic and assertions

When modifying tests:
1. Make your changes to the test files
2. Refresh the test-runner.html page in your browser
3. No need to restart the Python server for test file changes

## Troubleshooting

1. **"Connection refused" error**
   - Make sure you're running the Python server in the correct directory
   - Check if port 8000 is already in use (try a different port like 8080)

2. **"Failed to load resource" errors**
   - Verify your directory structure matches the one shown above
   - Check that all required JavaScript files are present in src/background/

3. **Test failures**
   - Check the browser console for detailed error messages
   - Verify the expected vs actual output in the test results
   - Make sure all required Turndown plugins are properly loaded

## Adding New Tests

To add a new test:
1. Add test HTML to `test-page.html`
2. Add test logic to `test-runner.html`
3. Refresh the browser to run the updated tests

## Current Test Coverage

- Basic Text Conversion
  - Headers
  - Italic text
  - Bold text
  - Bold-italic text
  - Strikethrough text
  - Line spacing and formatting

*More tests coming soon...*