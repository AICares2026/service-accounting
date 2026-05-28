## Stack
- C# / .NET (version undetected; check .csproj for TargetFramework)
- Docker (Dockerfile present)
- No test framework version detected; inspect .csproj for xUnit/NUnit/MSTest references

## Constraints
Never modify:
- `*.lock`, `packages.lock.json`, `package-lock.json` — lock files
- `**/Migrations/` — EF Core or any ORM migration files
- `**/*.Designer.cs`, `*.g.cs`, `*.generated.cs` — generated code
- `appsettings*.json` containing connection strings or secrets
- `.env`, `secrets.*`, any credential or certificate files
- `global.json` — pinned SDK version, do not change

## Conventions
- Solution follows standard .NET layout: `src/` for application code, `tests/` for test projects (verify actual structure before assuming)
- Test projects are named `*.Tests` or `*.Tests.csproj`
- One class per file; filename matches class name
- Docker image changes must not remove non-root USER instructions or add new capabilities

## Dependency manifests
- `**/*.csproj` — NuGet package references and TargetFramework
- `**/*.sln` — solution structure
- `global.json` — .NET SDK version pin
- `Dockerfile` — base image and runtime versions
