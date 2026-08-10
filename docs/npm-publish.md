# npm publish setup

shipkit uses **npm trusted publishing** (OIDC) from GitHub Actions — same as collab-kit.

## One-time setup

1. Sign in at [npmjs.com](https://www.npmjs.com/) as the `@korykaai` org owner
2. Go to **Access** → **Publishing access** → **Trusted publishers**
3. Add a trusted publisher:
   - **Organization / user:** `kory-kaai`
   - **Repository:** `shipkit`
   - **Workflow filename:** `publish-npm.yml`
   - **Environment:** (leave empty unless you use one)

4. Create the package entry (first publish establishes it):
   ```bash
   npm login
   cd shipkit
   npm publish --access public
   ```
   Or re-run the GitHub release workflow after trusted publishing is configured.

## Verify

```bash
npm view @korykaai/shipkit version
npx @korykaai/shipkit --help
```

## Re-publish after setup

Re-run the failed workflow or create a patch release:

```bash
gh workflow run publish-npm.yml -R kory-kaai/shipkit
```

Or bump to `0.1.1` and create a new GitHub release.
