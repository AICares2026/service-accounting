## Stack
C# / .NET (version undetected — check .csproj TargetFramework), Docker. NuGet for package management.

## Constraints
Never modify:
- `*.lock` files (packages.lock.json, NuGet lock files)
- `Migrations/` directories and any file matching `*Migration*.cs` or `*_Migration*.cs`
- `*.Designer.cs` and other generated code (`.g.cs`, `.g.i.cs`)
- `appsettings.Production.json`, `appsettings.*.json` containing secrets or connection strings
- `docker-compose.override.yml` if present
- `.env` files and any file containing credentials or API keys

## Conventions
- Standard .NET project layout: source under `src/` or project-named directories, tests under `tests/` or `*.Tests/` projects
- Test projects named `*.Tests.csproj`; test classes use xUnit or NUnit conventions (check existing test files before adding)
- Dockerfile(s) live at repo root or per-service subdirectory — match existing placement when adding new ones
- Follow existing namespace and folder structure; do not reorganise files without explicit instruction

## Dependency manifests
- `*.csproj` — NuGet package references (`<PackageReference>` elements)
- `packages.lock.json` — locked NuGet versions (do not edit directly; regenerate via `dotnet restore --use-lock-file`)
- `global.json` — .NET SDK version pin if present
- `Directory.Packages.props` — central package version management if present
