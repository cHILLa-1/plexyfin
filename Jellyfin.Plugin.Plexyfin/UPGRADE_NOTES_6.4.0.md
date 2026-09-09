# Plexyfin v6.4.0 - Jellyfin v12 Compatibility Release

## Overview
This release updates Plexyfin plugin to support Jellyfin v12.x while maintaining backward compatibility with core API functionality.

## Changes

### Version Information
- **Plugin Version**: 6.4.0 (up from 0.6.3.0)
- **Target Jellyfin Version**: 12.0.0.0 and above
- **.NET Target**: 8.0

### Dependencies Updated
```
Jellyfin.Controller: 10.10.7 → 12.0.0
Jellyfin.Model: 10.10.7 → 12.0.0
```

### Compatibility
- ✅ IScheduledTask interface - compatible with v12
- ✅ ICollectionManager - no breaking changes
- ✅ ILibraryManager - compatible API
- ✅ IProviderManager - compatible API
- ✅ IFileSystem - compatible API
- ✅ Authorization policies ("RequiresElevation") - unchanged
- ✅ BasePlugin<T> pattern - unchanged
- ✅ IHasWebPages interface - compatible
- ✅ External ID (ProviderIds) handling - unchanged

### Files Modified
1. `Jellyfin.Plugin.Plexyfin.csproj`
   - AssemblyVersion: 0.6.3.0 → 6.4.0
   - FileVersion: 0.6.3.0 → 6.4.0
   - Jellyfin.Controller: 10.10.7 → 12.0.0
   - Jellyfin.Model: 10.10.7 → 12.0.0

2. `Jellyfin.Plugin.Plexyfin/meta.json`
   - version: 0.6.3.0 → 6.4.0
   - targetAbi: 10.10.0.0 → 12.0.0.0

3. `Jellyfin.Plugin.Plexyfin/Plugin.cs`
   - Version log message updated to 6.4.0

### Installation
1. Rebuild the plugin with the updated dependencies
2. Install on Jellyfin v12.0.0 or higher
3. Existing configurations will be automatically compatible

### API Endpoints (Unchanged)
- `POST /Plexyfin/sync` - Sync collections and artwork
- `GET /Plexyfin/sync-status/{syncId}` - Check sync status
- `GET /Plexyfin/test-connection` - Test Plex server connection
- `POST /Plexyfin/DryRunSync` - Preview changes
- `POST /Plexyfin/UpdateSelectedLibraries` - Configure libraries

### Breaking Changes
**None** - All core functionality remains compatible with Jellyfin v10.x API patterns used in this plugin.

### Testing
Recommended tests:
- [ ] Connection test to Plex server
- [ ] Dry run sync to verify item matching
- [ ] Full collection sync
- [ ] Artwork sync (posters, backdrops, season art)
- [ ] Scheduled sync trigger
- [ ] Configuration persistence

### Notes
- Plugin retains full backward compatibility with existing Jellyfin v10.x installations if dependencies remain unchanged
- For Jellyfin v10.x deployment, use version 0.6.3.0 or earlier
- For Jellyfin v12.x deployment, use version 6.4.0 or later

