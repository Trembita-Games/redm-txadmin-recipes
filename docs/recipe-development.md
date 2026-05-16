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

## Official References

- [Official txAdmin Recipe Documentation](https://github.com/tabarra/txAdmin/blob/master/docs/recipe.md)
- [Official txAdmin Recipes Repository](https://github.com/citizenfx/txAdmin-recipes)
- [VORP txAdmin Recipe Reference](https://github.com/VORPCORE/VORP_txAdmin)

Use the official txAdmin documentation as the primary source for supported recipe actions, placeholders and deployment behavior.

Use existing community recipes only as references for structure and validation patterns.

---

## Repository Boundaries

Recipes belong in:

```txt
recipes/
```

Current recipe layout:

```txt
recipes/
├── vanilla/
│   └── recipe.yaml
└── trembita/
    └── recipe.yaml
```

Configuration templates belong in:

```txt
templates/
```

Current template layout:

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

Documentation belongs in:

```txt
docs/
```

Runtime data must not be committed.

---

## Recipe Variants

Current recipe variants:

```txt
recipes/vanilla/recipe.yaml
recipes/trembita/recipe.yaml
```

### `recipes/vanilla/recipe.yaml`

Clean vanilla RedM/RDR2 deployment using upstream Cfx.re server data resources.

This recipe should remain focused on the base vanilla server setup.

### `recipes/trembita/recipe.yaml`

Trembita Games deployment variant intended to use curated resources from:

```txt
redm-server-data
```

This recipe is intended for future Trembita Games server data deployments.

---

## Template Strategy

Shared templates should be placed in:

```txt
templates/common/
```

Use shared templates for configuration files that are identical across recipe variants.

Current shared templates:

```txt
templates/common/permissions.cfg
templates/common/secrets.cfg
```

Recipe-specific templates should be placed in:

```txt
templates/<recipe-name>/
```

Current recipe-specific templates:

```txt
templates/vanilla/server.cfg
templates/trembita/server.cfg
```

This keeps common configuration centralized and avoids duplicating identical files across recipes.

---

## Secrets Handling

Secrets should not be placed directly into `server.cfg`.

Recipes should generate:

```txt
secrets.cfg
```

from:

```txt
templates/common/secrets.cfg
```

The generated `server.cfg` should execute:

```cfg
exec secrets.cfg
```

The shared `secrets.cfg` template contains txAdmin variables:

```cfg
sv_licenseKey "{{svLicense}}"
set steam_webApiKey "{{steam_webApiKey}}"
```

Recipes must run variable replacement after generating `secrets.cfg`.

Example:

```yaml
- action: replace_string
  mode: all_vars
  file: ./secrets.cfg
```

---

## Permissions Handling

Permissions should be generated from:

```txt
templates/common/permissions.cfg
```

The generated `server.cfg` should execute:

```cfg
exec permissions.cfg
```

Admin principals should be generated through txAdmin using:

```cfg
{{addPrincipalsMaster}}
```

inside the recipe-specific `server.cfg` template.

---

## Versioning

Recipes should prefer stable release/tag URLs over moving `main` branch URLs when possible.

Preferred:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/v0.1.6/recipes/vanilla/recipe.yaml
```

Avoid for stable deployments:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/main/recipes/vanilla/recipe.yaml
```

Using tags helps prevent deployments from breaking unexpectedly when repositories change.

---

## Internal Repository References

Recipes may download this repository to access templates.

Example:

```yaml
- action: download_github
  src: https://github.com/Trembita-Games/redm-txadmin-recipes
  ref: v0.1.5
  dest: ./temp/redm-txadmin-recipes
```

When creating a new release, make sure recipe references are updated to the same release tag.

---

## Resource Ownership

Do not vendor third-party resources directly in this repository.

If a recipe references external resources, document:

- source repository
- purpose
- license considerations
- whether it is required or optional

Default Cfx.re resources should remain sourced from upstream Cfx.re/CitizenFX sources unless a separate licensing and ownership decision is made.

---

## Validation Checklist

Before marking a recipe as stable:

- [ ] txAdmin accepts the recipe URL
- [ ] deployment completes without manual file edits
- [ ] generated `server.cfg` contains required RedM configuration
- [ ] generated `permissions.cfg` exists
- [ ] generated `secrets.cfg` exists
- [ ] variables inside `secrets.cfg` are replaced
- [ ] resources are installed
- [ ] server starts
- [ ] license key is applied correctly
- [ ] Steam Web API key is applied correctly if provided
- [ ] admin principals are applied correctly
- [ ] RedM client can connect
- [ ] logs do not show missing required resources
