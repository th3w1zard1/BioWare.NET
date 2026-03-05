# Releasing BioWare.NET

NuGet publishing is automated through GitHub Actions.

## One-time setup

Add this repository secret in GitHub:

- `NUGET_API_KEY`: an API key with permission to push `BioWare.NET`

## Standard release flow

1. Make sure `ci.yml` is green on the branch you want to release.
2. Merge to the default branch.
3. Create and push a git tag:

   ```bash
   git tag v2.0.0
   git push origin v2.0.0
   ```

   Prerelease tags are supported too:

   ```bash
   git tag v2.0.0-beta.1
   git push origin v2.0.0-beta.1
   ```

4. GitHub Actions will:
   - restore dependencies
   - build the library
   - run tests
   - pack `BioWare.NET`
   - publish the `.nupkg` to NuGet with `--skip-duplicate`

## Manual publishing

The `publish-nuget.yml` workflow also supports `workflow_dispatch` with a `version` input.

## Local dry run

```bash
dotnet pack src/BioWare/BioWare.csproj -c Release -p:Version=2.0.0-local
```

## Notes

- The package version comes from the git tag or workflow input.
- The assembly name remains `BioWare` for source compatibility.
- The NuGet package ID is `BioWare.NET`.
