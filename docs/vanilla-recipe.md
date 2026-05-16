# Vanilla Recipe

Documentation for the vanilla RedM/RDR2 txAdmin recipe.

Recipe file:

```txt
recipes/vanilla.yaml
```

---

## Purpose

The vanilla recipe is intended to deploy a minimal RedM/RDR2 server through txAdmin.

It should provide:

- basic RedM server configuration
- default Cfx.re resources
- `set gamename rdr3`
- RedM session manager
- txAdmin placeholders
- minimal permissions configuration
- generated secrets configuration

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

## Generated Configuration Files

### `server.cfg`

Main server configuration.

It contains:

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
templates/vanilla/permissions.cfg
```

### `secrets.cfg`

Deployment-specific secrets generated from:

```txt
templates/vanilla/secrets.cfg
```

It contains:

```cfg
sv_licenseKey "{{svLicense}}"
set steam_webApiKey "{{steam_webApiKey}}"
```

The Steam Web API key is provided through the recipe variable:

```yaml
variables:
  steam_webApiKey: "none"
```

---

## Relationship to redm-vanilla-template

`redm-vanilla-template` provides a Git-first development workflow.

This recipe provides a txAdmin-first deployment workflow.

Both should remain compatible, but they do not need to share identical file layout.

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
- default resources are installed
- server starts
- RedM client can connect
- no required config is missing
- license key is correctly written as `sv_licenseKey "..."`
- Steam Web API key is correctly written as `set steam_webApiKey "..."`