# Database Plus

一款非常好用的关系型数据库和非关系型数据库 IDEA 插件。

Database Plus is a commercial-grade JetBrains database tool plugin implemented in Kotlin.

Current development mode intentionally keeps paid feature gates open:

- `DatabasePlusSettings.developmentLicenseBypass = true`
- `DatabasePlusSettings.enforceMarketplaceLicense = false`

This lets local testing run without a JetBrains Marketplace license/pass. When the plugin is close to release, turn on **Settings | Database Plus | Enforce Marketplace license checks** and wire `LicenseService` to the Marketplace license API/sandbox flow.

## Marketplace (Hanghang vendor)

Release materials live in [`docs/marketplace/`](docs/marketplace/):

| File | Purpose |
|------|---------|
| `EULA.md` | Developer EULA for listing |
| `PRIVACY_POLICY.md` | Privacy policy for listing |
| `PRODUCT_CODE_REQUEST_EMAIL.md` | Email template to **marketplace@jetbrains.com** |
| `RELEASE_CHECKLIST.md` | Pre-release checklist |
| `LISTING_DESCRIPTION.md` | Marketplace page copy draft |
| `THIRD_PARTY_NOTICES.md` | JDBC/driver license notes |

**Product code:** `PDATABASEPLUS` (pending JetBrains registration confirmation).

**Development mode** (default): `developmentLicenseBypass = true`, `enforceMarketplaceLicense = false`.

**Release mode:** turn off bypass, enable enforce, test on Marketplace Demo, then `gradle publishPlugin` (see `gradle.properties.example`).

## Implemented Development Preview

- JetBrains plugin scaffold with ToolWindow, actions, settings, services, and icon.
- Data source CRUD with PasswordSafe-backed password storage.
- JDBC connection manager and dialect registry.
- Support matrix scaffolding for MySQL, MariaDB, PostgreSQL, SQLite, SQL Server, Oracle, H2, DuckDB, ClickHouse, and Generic JDBC.
- Lazy database explorer for data sources, schemas, tables/views, and columns.
- SQL console with execution, cancellation, max rows, query history, dangerous SQL confirmation, and result grid.
- Result grid export to CSV, JSON, Markdown, SQL INSERT, and basic XLSX.
- CSV import preview path that generates INSERT SQL for review before execution.
- Editable table result mode with primary-key-based commit and rollback-on-error.
- DDL fallback generation.
- Basic ER diagram generation and PNG export.
- Basic Schema Diff with migration SQL draft output.
- Unit tests for SQL splitting, safety detection, and import/export helpers.

## Build Notes

The project uses IntelliJ Platform Gradle Plugin 2.x and targets IntelliJ Platform 2024.2+.

This machine currently has Java 17 but no global `gradle` or `kotlinc` command. A cached Gradle 8.14.3 distribution exists, but the sandbox blocks Gradle's local daemon loopback, so command-line verification could not be completed here. Open the folder in IntelliJ IDEA and import it as a Gradle project, or install/use Gradle 8.14+ and run:

```powershell
gradle test
gradle buildPlugin
gradle runIde
```

Before publishing, run:

```powershell
gradle verifyPlugin
```
