# Recipes

txAdmin recipe files.

---

## Available Recipes

```txt
recipes/
├── vanilla/
│   └── recipe.yaml
└── trembita/
    └── recipe.yaml
```

---

## Vanilla Recipe

Path:

```txt
recipes/vanilla/recipe.yaml
```

Purpose:

```txt
Clean vanilla RedM/RDR2 deployment using upstream Cfx.re server data resources.
```

Example raw URL:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/main/recipes/vanilla/recipe.yaml
```

Stable release URL format:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/<tag>/recipes/vanilla/recipe.yaml
```

---

## Trembita Recipe

Path:

```txt
recipes/trembita/recipe.yaml
```

Purpose:

```txt
Trembita Games deployment variant intended to use curated resources from redm-server-data.
```

Example raw URL:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/main/recipes/trembita/recipe.yaml
```

Stable release URL format:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/<tag>/recipes/trembita/recipe.yaml
```

---

## Current Status

The vanilla recipe is under active validation.

The Trembita recipe is reserved for the Trembita Games deployment variant and will be expanded when `redm-server-data` contains validated resources.

---

## Usage

In txAdmin:

```txt
txAdmin -> Deployer -> Custom Recipe
```

Use a raw GitHub URL.

Example for vanilla:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/main/recipes/vanilla/recipe.yaml
```

After stable releases are available, prefer release tag URLs instead of `main`.

---

## Recipe Requirements

Recipes should:

- deploy into a clean txAdmin server data directory
- create `server.cfg`
- create `permissions.cfg`
- create `secrets.cfg`
- create or download `resources/`
- clean temporary files
- avoid committing runtime state
- avoid copying third-party source code into this repository

---

## Notes

Recipe files should stay focused on deployment orchestration.

Server configuration content should live in:

```txt
templates/
```