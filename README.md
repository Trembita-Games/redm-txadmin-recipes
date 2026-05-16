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
- gameplay resources
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

## Recipes

Available recipes:

- [Vanilla Recipe](docs/vanilla-recipe.md)
- `recipes/vanilla.yaml`
- `recipes/trembita.yaml`

Current status:

```txt
Initial structure / not fully validated yet
```

---

## Important Notice

This repository does not vendor third-party resources.

Recipes may reference external repositories or source archives, but this repository should not copy third-party source code directly.

Default Cfx.re resources should remain sourced from upstream Cfx.re/CitizenFX sources.

---

## Repository Structure

```txt
docs/       -> Documentation for recipes and development
recipes/    -> txAdmin recipe YAML files
templates/  -> Server configuration templates used by recipes
examples/   -> Example usage notes
```

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

This repository is in the initial foundation phase.

The next step is to validate the `vanilla.yaml` recipe in a clean txAdmin deployment directory.

---

## License

MIT License