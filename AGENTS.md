## Stack
C# / .NET (version undetected), Docker. Check `.csproj` files for exact SDK and package versions.

## Constraints
Never modify:
- `*.lock`, `packages.lock.json`, `package-lock.json`
- `**/Migrations/**` — EF Core or any DB migration files
- `**/*.Designer.cs`, `*.g.cs`, `*.generated.cs` — generated code
- `Dockerfile.base` or any base image definitions if present
- `appsettings.Production.json`, `secrets.json`, `*.pfx`, `*.pem`, `*.key`
- `.git/**`

## Conventions
- C# source lives under `src/` or project-named subdirectories; follow existing namespace pattern
- Test projects are suffixed `.Tests` or `.UnitTests`; test files are suffixed `Tests.cs`
- One class per file; filename matches class name exactly
- Docker images: do not change base image tags without confirming compatibility with the .NET version in `.csproj`
- Dead code removal: only remove symbols with zero references confirmed via static analysis; never remove `public` API surface without explicit confirmation

## Dependency manifests
- `**/*.csproj` — NuGet package references and SDK version
- `**/Directory.Packages.props` — central package management if present
- `**/global.json` — .NET SDK pin
- `**/Dockerfile` — base image and layer dependencies
