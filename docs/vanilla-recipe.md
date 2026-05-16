# Vanilla Recipe

Documentation for the vanilla RedM/RDR2 txAdmin recipe.

Recipe file:

```txt
recipes/vanilla/recipe.yaml
```

---

## Purpose

The vanilla recipe is intended to deploy a minimal RedM/RDR2 server through txAdmin.

It provides:

- basic RedM server configuration
- default Cfx.re resources
- `set gamename rdr3`
- RedM session manager
- txAdmin placeholders
- shared permissions configuration
- generated secrets configuration

---

## Recipe URL

Using `main`:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/main/recipes/vanilla/recipe.yaml
```

Using a release tag:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/v0.1.7/recipes/vanilla/recipe.yaml
```

For stable deployments, prefer release tags.

---

## Expected Output

A txAdmin deployment should create a server data directory containing:

```txt
server.cfg
permissions.cfg
secrets.cfg
resources/
```

The generated `server.cfg` should be compatible with txAdmin and should not depend on local Git-first files like:

```txt
local.cfg
permissions.cfg.example
```

---

## Source Templates

The vanilla recipe uses these templates:

```txt
templates/vanilla/server.cfg
templates/common/permissions.cfg
templates/common/secrets.cfg
```

### `templates/vanilla/server.cfg`

Recipe-specific main server configuration.

### `templates/common/permissions.cfg`

Shared permissions configuration reused by multiple recipe variants.

### `templates/common/secrets.cfg`

Shared secrets configuration reused by multiple recipe variants.

---

## Generated Configuration Files

### `server.cfg`

Main server configuration.

It contains txAdmin-generated values and executes shared generated files:

```cfg
set gamename rdr3
{{serverEndpoints}}
sv_maxclients {{maxClients}}
exec permissions.cfg
exec secrets.cfg
{{addPrincipalsMaster}}
```

### `permissions.cfg`

Base permission configuration generated from:

```txt
templates/common/permissions.cfg
```

Current content includes:

```cfg
add_ace group.admin command allow
add_ace resource.mapmanager command allow
```

### `secrets.cfg`

Deployment-specific secrets generated from:

```txt
templates/common/secrets.cfg
```

It contains:

```cfg
sv_licenseKey "{{svLicense}}"
set steam_webApiKey "{{steam_webApiKey}}"
```

The Steam Web API key is provided through the recipe variable:

```yaml
variables:
  steam_webApiKey: ""
```

The recipe must run variable replacement after generating `secrets.cfg`:

```yaml
- action: replace_string
  mode: all_vars
  file: ./secrets.cfg
```

---

## Relationship to redm-vanilla-template

`redm-vanilla-template` provides a Git-first development workflow.

This recipe provides a txAdmin-first deployment workflow.

Both should remain compatible, but they do not need to share identical file layout.

Key difference:

```txt
redm-vanilla-template:
  server.cfg -> exec local.cfg

redm-txadmin-recipes:
  server.cfg -> exec secrets.cfg
```

---

## Data Folder Name

txAdmin uses the recipe metadata field:

```yaml
name: Trembita-RDR2
```

to generate the deployment `.base` folder name.

Expected folder name format:

```txt
Trembita-RDR2_<txadmin-generated-suffix>.base
```

The suffix is controlled by txAdmin.

---

## Current Status

```txt
Validation version
```

Before marking this recipe as stable, validate:

- txAdmin can load the recipe
- deployment completes
- `server.cfg` is generated
- `permissions.cfg` is generated
- `secrets.cfg` is generated
- variables inside `secrets.cfg` are replaced
- default resources are installed
- server starts
- RedM client can connect
- no required config is missing
- license key is correctly written as `sv_licenseKey "..."`
- Steam Web API key is correctly written as `set steam_webApiKey "..."`
- admin principals are generated correctly
