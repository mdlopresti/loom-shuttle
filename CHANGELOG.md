# Changelog

All notable changes to Shuttle (CLI) will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.2.0] - 2025-12-12

### Changed
- **Standalone Repository**: Shuttle has been split from the loom-weft monorepo into its own repository
- **Package Source**: Now published as a standalone package (previously part of monorepo)
- Version bumped to 0.2.0 to signal the repository split

### Migration from Monorepo

If you were using `@loom/shuttle` from the monorepo:

```bash
# Uninstall old version
npm uninstall -g @loom/shuttle

# Install new standalone version
npm install -g @loom/shuttle
```

Your configuration (`~/.loom/config.json`) is fully compatible - no changes needed.

### No Breaking Changes
- All commands work identically
- All CLI flags unchanged
- Configuration format unchanged
- API compatibility maintained

---

## [0.1.4] - 2025-12-12

### Added
- **Channels commands**: New `shuttle channels list` and `shuttle channels read <channel>` commands

---

## [0.1.0] - 2025-12-11

### Status: Beta Release

This release marks the transition from Alpha to Beta. Core CLI functionality has been tested against Weft coordinator.

### Added
- **REST API client**: All commands now use Weft REST API instead of direct NATS
- **Work submission**: `shuttle submit` with boundary, capability, priority, deadline options
- **Agent management**: `shuttle agents list` with filtering by type, status, capability
- **Work monitoring**: `shuttle work list`, `shuttle work show`, `shuttle work cancel`
- **Real-time watch**: `shuttle watch <work-id>` for progress monitoring
- **Target management**: Full CRUD for spin-up targets (add, show, update, remove, enable, disable, test)
- **Statistics**: `shuttle stats` shows coordinator metrics
- **Projects**: `shuttle projects` lists active projects in multi-tenant mode
- **Configuration**: `shuttle config` for managing CLI settings
- **Output formats**: Table (default) and JSON (`--json` flag)
- **Global options**: `--project`, `--config`, `--quiet`

### Changed
- Migrated from direct NATS to REST API communication
- Renamed `classification` to `boundary` for work routing
- Commands now require Weft coordinator to be running

### Integration Tests Passed
- 5/5 Configuration tests (REQ-CLI-CFG)
- 3/3 Agent command tests (REQ-CLI-AGENT)
- 3/3 Work command tests (REQ-CLI-WORK)
- 4/4 Target command tests (REQ-CLI-TARGET)
- 2/2 Stats/Projects tests (REQ-CLI-INFO)
- JSON output verified across all commands

### Known Limitations
- No offline mode
- No batch operations
- Watch uses polling (no streaming)
- Interactive mode has basic validation

---

[0.2.0]: https://github.com/mdlopresti/loom-shuttle/releases/tag/v0.2.0
[0.1.4]: https://github.com/mdlopresti/loom-weft/releases/tag/v0.1.4
[0.1.0]: https://github.com/mdlopresti/loom-weft/releases/tag/v0.1.0
