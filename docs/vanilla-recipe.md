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

---

## Expected Output

A txAdmin deployment should create a server data directory containing:

```txt
server.cfg
permissions.cfg
resources/
```

The generated `server.cfg` should be compatible with txAdmin and should not depend on local Git-first files like:

```txt
local.cfg
permissions.cfg.example
```

---

## Relationship to redm-vanilla-template

`redm-vanilla-template` provides a Git-first development workflow.

This recipe provides a txAdmin-first deployment workflow.

Both should remain compatible, but they do not need to share identical file layout.

---

## Current Status

```txt
Initial template / not fully validated yet
```

Before marking this recipe as stable, validate:

- txAdmin can load the recipe
- deployment completes
- `server.cfg` is generated
- default resources are installed
- server starts
- RedM client can connect
- no required config is missing