# Templates

Configuration templates used by txAdmin recipes.

---

## Structure

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

---

## Purpose

Templates keep recipe YAML files smaller and easier to read.

They also make server configuration easier to review separately from deployment logic.

---

## Common Templates

Shared templates are stored in:

```txt
templates/common/
```

Current shared templates:

```txt
permissions.cfg
secrets.cfg
```

These files are reused by both vanilla and Trembita recipe variants.

---

## Recipe-Specific Templates

Recipe-specific server configuration files are stored in:

```txt
templates/vanilla/server.cfg
templates/trembita/server.cfg
```

### Vanilla

```txt
templates/vanilla/server.cfg
```

Used by:

```txt
recipes/vanilla/recipe.yaml
```

Purpose:

```txt
Clean vanilla RedM/RDR2 server configuration.
```

### Trembita

```txt
templates/trembita/server.cfg
```

Used by:

```txt
recipes/trembita/recipe.yaml
```

Purpose:

```txt
Trembita Games server configuration intended for curated server data resources.
```

---

## Secrets Template

The shared secrets template is:

```txt
templates/common/secrets.cfg
```

It contains txAdmin variables:

```cfg
sv_licenseKey "{{svLicense}}"
set steam_webApiKey "{{steam_webApiKey}}"
```

Recipes must run variable replacement after generating `secrets.cfg`.

Example recipe task:

```yaml
- action: replace_string
  mode: all_vars
  file: ./secrets.cfg
```

---

## Permissions Template

The shared permissions template is:

```txt
templates/common/permissions.cfg
```

It contains base permission rules for generated server deployments.

---

## Notes

Templates are intended for txAdmin recipe generation.

They are not the same as the Git-first configuration files in `redm-vanilla-template`.

Do not place runtime secrets directly in template files.