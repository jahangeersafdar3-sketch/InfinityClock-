# Infinity Clock — Stage 16

## Live Wallpaper Pro
- User-configurable quality: Battery/Balanced/Smooth.
- Effects: Clean/Glow/Aurora.
- Adjustable dim overlay.
- Official Android WallpaperService settingsActivity.
- Visibility-aware rendering and callback cleanup.
- Existing clock selection and offline behavior preserved.

### Test contract
1. Open Settings → Set Live Wallpaper.
2. In wallpaper preview open settings and change quality/effect/dim.
3. Apply wallpaper, leave/return to launcher, then reopen settings.
4. Verify the renderer pauses when wallpaper is not visible.
5. Switch between digital/analog/hybrid selected clocks and verify wallpaper follows selection.
6. Verify no network is required.
