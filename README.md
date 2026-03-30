# K-Map Solver

A comprehensive web-based Karnaugh Map (K-Map) solver for digital logic design. This tool helps minimize Boolean expressions using the Quine-McCluskey algorithm with visual K-map representation.

## Features

- **Variable Support**: 2 to 6 variables
- **Multiple Input Methods**:
  - Minterm notation (e.g., `0,1,2,3,5,7`)
  - Range input (e.g., `0-3,5,7-9`)
- **Don't Care Conditions**: Include X values with `dontcares` field
- **Visual K-Map Display**:
  - Color-coded groups
  - Gray code ordering
  - Cell indices for reference
- **Algorithm Visualization**: Step-by-step Quine-McCluskey implementation
- **Minimized Expressions**:
  - SOP (Sum of Products)
  - POS (Product of Sums)
- **Statistics**: Number of literals, prime implicants, essential primes
- **Export Options**: LaTeX, Text, JSON, Clipboard

## Quick Start

1. **Open the website**:

2. **Enter minterms**: Type comma-separated decimal values (e.g., `0,1,2,3,5,7`)

3. **Optional**: Add don't care conditions (e.g., `4,6`)

4. **Click "Solve K-Map"** to see:
   - Visual K-map with groups
   - Minimized SOP and POS expressions
   - Algorithm steps
   - Statistics

## Examples

### 2-variable K-map
- Input: `0,1,2,3` (all minterms)
- Output: `SOP: A' + B'` (simplified)

### 3-variable K-map
- Input: `0,1,2,3,5,7`
- Groups: {0,1,2,3} and {3,5,7}
- Output: `SOP: A'B' + B` or similar

### With Don't Cares
- Minterms: `0,1,2,4,5`
- Don't cares: `3,6,7`
- Enables larger groups for better minimization

## How It Works

### 1. Input Parsing
- Minterms are parsed and validated
- Don't care conditions are separated
- Variables count determines K-map dimensions

### 2. K-Map Construction
- Gray code ordering for rows and columns
- Adjacent cells differ by only one bit
- Wrap-around adjacency is supported

### 3. Quine-McCluskey Algorithm
- Group minterms by number of 1s
- Combine adjacent terms iteratively
- Identify prime implicants
- Build prime implicant chart
- Find essential prime implicants

### 4. Group Visualization
- Greedy algorithm finds maximal groups
- Groups must be powers of 2 (1, 2, 4, 8, ...)
- Wrap-around groups are detected
- Each group gets a unique color

### 5. Expression Generation
- Convert binary patterns to Boolean expressions
- SOP from prime implicants covering all minterms
- POS calculated using De Morgan's principle

## Export Formats

### LaTeX
Generates a complete LaTeX document with K-map table and results.

### Text
Plain text format suitable for documentation.

### JSON
Full data structure including all intermediate steps for further processing.

### Copy to Clipboard
Copies SOP and POS expressions for quick pasting.

## Technical Details

- **No dependencies**: Pure vanilla JavaScript
- **Responsive design**: Works on desktop and mobile
- **Modern CSS**: Grid layout, flexbox, CSS variables
- **Browser support**: All modern browsers (Chrome, Firefox, Safari, Edge)

## Algorithm Notes

The solver implements:
- **Quine-McCluskey**: Prime implicant generation
- **Prime Chart**: Essential prime identification
- **Greedy Grouping**: Visual group discovery (not necessarily optimal for POS)
- **Gray Code**: Adjacent cell relationship

### Limitations
- POS generation uses a secondary Quine-McCluskey on zeros; may not be minimal in all cases
- Group algorithm is greedy; finding the absolute minimal grouping with overlaps requires more complex optimization
- 5 and 6 variable K-maps are large (2x16 and 4x16 grids respectively)

## Future Enhancements

- [ ] Boolean expression parser (convert A'B+BC to minterms)
- [ ] Petrick's method for complete minimization
- [ ] Interactive K-map (click to toggle cells)
- [ ] Save/load state from localStorage
- [ ] Truth table generation
- [ ] Logic gate diagram
- [ ] Step-through algorithm animation
- [ ] Support for up to 8 variables

## Educational Value

This tool is designed for:
- Digital logic design courses
- Understanding Karnaugh maps
- Learning Quine-McCluskey algorithm
- Verifying manual minimization
- Computer organization/architecture labs


## Contributing

Contributions welcome! Feel free to:
- Report bugs
- Suggest features

## Version

v1.0.0 - Initial release
