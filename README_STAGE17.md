# Infinity Clock — Stage 17

## Premium UI/UX foundation
- Premium animated hero surface on the Home experience.
- Subtle animated emphasis with reduced-motion-safe single property animation.
- Premium status tag for core capabilities.
- No navigation/API contract changes; Stage 1–16 features preserved.
- Offline-first architecture preserved.

### Test contract
1. Launch on a mid-range Android phone and open every bottom tab.
2. Verify the Home hero animation remains smooth and does not block interaction.
3. Verify Studio/AI/Time Lab/Widgets/Wallpaper continue to open.
4. Switch dark/AMOLED settings and ensure readable contrast.
5. Run for several minutes and check for obvious jank or runaway UI work.
6. Build through GitHub Actions before moving to Stage 18.
