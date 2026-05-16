# Documentation

Documentation for `redm-txadmin-recipes`.

This repository contains txAdmin recipe documentation, deployment notes and troubleshooting guides for Trembita Games RedM/RDR2 servers.

---

## Guides

- [Vanilla Recipe](vanilla-recipe.md)
- [Recipe Development](recipe-development.md)
- [Troubleshooting](troubleshooting.md)

---

## Repository References

- [Root README](../README.md)
- [Recipes Directory](../recipes/README.md)
- [Templates Directory](../templates/README.md)
- [Examples](../examples/README.md)

---

## Related Repositories

- [`redm-vanilla-template`](https://github.com/Trembita-Games/redm-vanilla-template)
- [`redm-server-data`](https://github.com/Trembita-Games/redm-server-data)

---

## Recipe Layout

Recipes are grouped by deployment variant:

```txt
recipes/
├── vanilla/
│   └── recipe.yaml
└── trembita/
    └── recipe.yaml
```

### Vanilla

The vanilla recipe deploys a clean RedM/RDR2 baseline using upstream Cfx.re server data resources.

```txt
recipes/vanilla/recipe.yaml
```

### Trembita

The Trembita recipe is intended for future deployment using Trembita Games curated server data resources.

```txt
recipes/trembita/recipe.yaml
```

---

## Template Layout

Templates are grouped by shared and recipe-specific configuration:

```txt
templates/
├── common/
│   ├── permissions.cfg
│   └── secrets.cfg
├── vanilla/
│   └── server.cfg
└── trembita/
    └── server.cfg
```

Shared templates are reused by multiple recipes.

Recipe-specific `server.cfg` files are kept separate.

---

## Current Scope

This repository focuses on txAdmin recipe-based deployment.

It should remain separate from:

- local Git-first server startup scripts
- server resources
- custom gameplay systems
- RP frameworks

Those belong in other repositories.

---

## References

- [Official txAdmin Recipe Documentation](https://github.com/tabarra/txAdmin/blob/master/docs/recipe.md)
- [Official txAdmin Recipes Repository](https://github.com/citizenfx/txAdmin-recipes)
- [VORP txAdmin Recipe Reference](https://github.com/VORPCORE/VORP_txAdmin)
