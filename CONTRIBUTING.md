# Contributing

## Development workflow

1. Create a branch.
2. Run restore, build, and tests locally.
3. Keep changes scoped and documented.
4. Open a pull request once CI is green.

## Local commands

```bash
dotnet restore BioWare.NET.sln
dotnet build BioWare.NET.sln -c Release
dotnet test BioWare.NET.sln -f net9.0 -c Release
dotnet pack src/BioWare/BioWare.csproj -c Release -p:Version=2.0.0-local
```

## Guidelines

- Preserve compatibility with both `net9.0` and `net48`.
- Prefer additive API changes over breaking changes.
- Keep file format behavior compatible with existing Odyssey/BioWare tooling.
- Add or update tests when fixing serialization, parsing, or patching behavior.
- Avoid introducing runtime dependencies on the broader Andastra engine.

## Release notes

NuGet publishing is tag-driven. See [docs/RELEASING.md](docs/RELEASING.md).
