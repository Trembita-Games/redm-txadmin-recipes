# Recipe Development

Guidelines for developing txAdmin recipes in this repository.

---

## Goals

Recipes should be:

- predictable
- minimal
- reproducible
- easy to validate
- compatible with txAdmin
- safe for public open-source usage

---

## Repository Boundaries

Recipes belong in:

```txt
recipes/
```

Configuration templates belong in:

```txt
templates/
```

Documentation belongs in:

```txt
docs/
```

Runtime data must not be committed.

---

## Versioning

Recipes should prefer stable release/tag URLs over moving `main` branch URLs when possible.

Preferred:

```txt
https://raw.githubusercontent.com/Trembita-Games/example-repo/v0.1.0/file
```

Avoid when possible:

```txt
https://raw.githubusercontent.com/Trembita-Games/example-repo/main/file
```

Using tags helps prevent deployments from breaking unexpectedly when repositories change.

---

## Resource Ownership

Do not vendor third-party resources directly in this repository.

If a recipe references external resources, document:

- source repository
- purpose
- license considerations
- whether it is required or optional

---

## Recipe Variants

Current planned recipe variants:

```txt
vanilla.yaml
trembita.yaml
```

### `vanilla.yaml`

Minimal RedM/RDR2 baseline deployment.

### `trembita.yaml`

Future recipe variant that may include Trembita Games server data resources from:

```txt
redm-server-data
```

---

## Official References

- [Official txAdmin Recipe Documentation](https://github.com/tabarra/txAdmin/blob/master/docs/recipe.md)
- [Official txAdmin Recipes Repository](https://github.com/citizenfx/txAdmin-recipes)
- [VORP txAdmin Recipe Reference](https://github.com/VORPCORE/VORP_txAdmin)

Use the official txAdmin documentation as the primary source for supported recipe actions, placeholders and deployment
behavior.

Use existing community recipes only as references for structure and validation patterns.

---

## Validation Checklist

Before marking a recipe as stable:

- [ ] txAdmin accepts the recipe
- [ ] deployment completes without manual file edits
- [ ] generated `server.cfg` contains required RedM configuration
- [ ] resources are installed
- [ ] server starts
- [ ] license key is applied correctly
- [ ] admin principals are applied correctly
- [ ] RedM client can connect
- [ ] logs do not show missing required resources