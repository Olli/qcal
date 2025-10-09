# qcal Agent Guidelines

## Build Commands
- Build: `make` (compiles to `qcal` binary)
- Clean: `make clean`
- Install: `sudo make install`
- Cross-platform: `make darwin` (macOS), `make linux-arm`, `make windows`

## Test Commands
- No test suite exists - add `*_test.go` files and run `go test ./...`

## Code Style Guidelines

### Imports
- Standard library imports first, sorted alphabetically
- Third-party imports second
- Blank line between import groups

### Formatting
- Use `gofmt` for consistent formatting
- 4-space indentation (Go standard)
- Line length: reasonable, break long lines

### Types & Naming
- Structs: PascalCase for exported fields (e.g., `Event`, `Href`, `Summary`)
- Functions: camelCase (e.g., `fetchCalData`, `createAppointment`)
- Constants: ALL_CAPS with underscores (e.g., `IcsFormat`, `ColDefault`)
- Variables: camelCase, descriptive names

### Error Handling
- Fatal errors: `log.Fatal(err)` (terminates program)
- Non-fatal: `checkError(e)` or return errors
- HTTP errors: check `resp.Status` after requests

### General
- Minimal comments - focus on complex logic only
- Use receiver methods for struct operations (e.g., `(e Event) fancyOutput()`)
- Global config variables acceptable for CLI tools
- Use `time.Time` for dates, parse with constants like `IcsFormat`