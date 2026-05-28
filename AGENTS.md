## Stack
C# / .NET (version undetected, check .csproj TargetFramework), Docker containers. NuGet for package management.

## Constraints
Never modify:
- `*.lock` files (packages.lock.json, any lockfiles)
- `**/Migrations/*.cs` — EF Core or other ORM migration files
- `**/*.Designer.cs`, `**/*.generated.cs` — generated code
- `appsettings*.json` containing connection strings or secrets
- `docker-compose.override.yml` if present (environment-specific overrides)
- `.github/` or any CI pipeline definitions unless the task explicitly targets them

## Conventions
- Solution structure follows standard .NET layout: `src/` for source projects, `tests/` for test projects (confirm actual dirs before writing)
- Test projects use xUnit or MSTest — match existing framework; do not introduce a second test framework
- Test class names mirror the class under test with a `Tests` suffix; method names follow `MethodName_Condition_ExpectedResult`
- One class per file; filename matches class name exactly

## Dependency manifests
- `**/*.csproj` — NuGet package references (`<PackageReference>` elements)
- `**/*.props` — shared version props if present (e.g., `Directory.Build.props`)
- `Dockerfile` / `docker-compose.yml` — base image versions; update `FROM` tags in these files only
