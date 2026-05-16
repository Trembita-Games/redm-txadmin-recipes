# redm-txadmin-recipes

txAdmin recipes for Trembita Games RedM/RDR2 server deployments.

This repository contains deployment recipes and configuration templates for setting up RedM/RDR2 servers through txAdmin.

---

## Purpose

`redm-txadmin-recipes` provides txAdmin-based deployment flows for the Trembita Games RedM/RDR2 ecosystem.

It is designed to work together with:

- [`redm-vanilla-template`](https://github.com/Trembita-Games/redm-vanilla-template)
- [`redm-server-data`](https://github.com/Trembita-Games/redm-server-data)

---

## Repository Role

This repository is responsible for:

- txAdmin recipes
- deployment templates
- server configuration templates for txAdmin
- documented setup flows
- future deployment variants

It is not responsible for:

- FXServer artifacts
- default Cfx.re resource ownership
- gameplay resource implementation
- RP frameworks
- database schema ownership
- server runtime state

---

## Deployment Modes

The Trembita Games RedM ecosystem supports multiple deployment modes.

### Git-first development flow

Use:

```txt
redm-vanilla-template
```

for local development, scripted setup and direct FXServer startup.

### txAdmin deployment flow

Use this repository for txAdmin recipe-based deployment.

This is intended for:

- server setup through txAdmin UI
- easier server management
- deployment experiments
- future production-style deployment flows

---

## Available Recipes

### Vanilla Recipe

Path:

```txt
recipes/vanilla/recipe.yaml
```

Purpose:

```txt
Clean vanilla RedM/RDR2 deployment using upstream Cfx.re server data resources.
```

Raw URL format:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/<tag-or-branch>/recipes/vanilla/recipe.yaml
```

Example using `main`:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/main/recipes/vanilla/recipe.yaml
```

### Trembita Recipe

Path:

```txt
recipes/trembita/recipe.yaml
```

Purpose:

```txt
Trembita Games deployment variant intended to use curated resources from redm-server-data.
```

Raw URL format:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/<tag-or-branch>/recipes/trembita/recipe.yaml
```

Example using `main`:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/main/recipes/trembita/recipe.yaml
```

---

## Recommended Usage

For testing, using `main` is acceptable.

For stable deployments, prefer release tags.

Example:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/v0.1.6/recipes/vanilla/recipe.yaml
```

Using tags prevents deployments from unexpectedly changing when `main` changes.

---

## Repository Structure

```txt
docs/       -> Documentation for recipes and development
recipes/    -> txAdmin recipe YAML files
templates/  -> Server configuration templates used by recipes
examples/   -> Example usage notes
```

Current recipe/template layout:

```txt
recipes/
├── vanilla/
│   └── recipe.yaml
└── trembita/
    └── recipe.yaml

templates/
├── common/
│   ├── permissions.cfg
│   └── secrets.cfg
├── vanilla/
│   └── server.cfg
└── trembita/
    └── server.cfg
```

---

## Template Strategy

Shared configuration templates are stored in:

```txt
templates/common/
```

Recipe-specific server configuration templates are stored in:

```txt
templates/vanilla/
templates/trembita/
```

This avoids duplicating identical files such as:

```txt
permissions.cfg
secrets.cfg
```

---

## Important Notice

This repository does not vendor third-party resources.

Recipes may reference external repositories or source archives, but this repository should not copy third-party source code directly.

Default Cfx.re resources should remain sourced from upstream Cfx.re/CitizenFX sources unless a separate licensing and ownership decision is made.

---

## Documentation

- [Documentation Index](docs/README.md)
- [Vanilla Recipe](docs/vanilla-recipe.md)
- [Recipe Development](docs/recipe-development.md)
- [Troubleshooting](docs/troubleshooting.md)

---

## References

- [Official txAdmin Recipe Documentation](https://github.com/tabarra/txAdmin/blob/master/docs/recipe.md)
- [Official txAdmin Recipes Repository](https://github.com/citizenfx/txAdmin-recipes)
- [VORP txAdmin Recipe Reference](https://github.com/VORPCORE/VORP_txAdmin)

---

## Current Status

This repository is in active recipe validation.

The vanilla recipe is the first recipe being validated.

The Trembita recipe is intended for future deployment with curated Trembita Games server data resources.

---

## License

MIT License
