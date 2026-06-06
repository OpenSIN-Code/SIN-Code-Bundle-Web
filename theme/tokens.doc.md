# web/theme/tokens — Design tokens (shared with TUI)

## What
CSS custom-property tokens for the Bundle-Web GUI. **Same color story as the
Bubbletea TUI** (Go side: `internal/tui/theme/tokens.go`) so the two UIs feel
like one product.

## How to use
Import once at the top of `app/globals.css`:

```css
@import "../../theme/tokens.css";
```

Then reference via `var(--sin-color-primary)` etc. in Tailwind config or
inline styles.

## Token groups
- **Color**: `--sin-color-{base,surface,text,primary,accent,success,warning,danger,...}`
- **Spacing**: `--sin-space-{0..8}` (4px grid, max 64px)
- **Radius**: `--sin-radius-{sm,md,lg,xl}`
- **Typography**: `--sin-font-{sans,mono}`, `--sin-text-{xs..3xl}`
- **Motion**: `--sin-duration-{fast,base,slow}`, `--sin-ease-{in,out,io}`

## Why HSL not hex
HSL lets us derive hover/focus/active states with `hsl(from var(--sin-color-primary) h s l / 0.8)`.
Hex tokens would require N variants for N states.

## Sync rule
When you change `--sin-color-primary` here, mirror it in
`SIN-Code-Bundle/internal/tui/theme/tokens.go` `Palette.Primary`.
Both repos have a CI check that compares the two files.

## Related
- `../internal/tui/theme/tokens.go` — Go mirror
- `../app/globals.css` — where the tokens are loaded
- `../tailwind.config.ts` — extends with `var(--sin-color-*)`
