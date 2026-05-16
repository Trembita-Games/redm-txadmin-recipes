# Examples

Example usage notes for `redm-txadmin-recipes`.

---

## Loading a Custom Recipe

In txAdmin:

```txt
txAdmin -> Deployer -> Custom Recipe
```

Use a raw GitHub URL.

---

## Vanilla Recipe Example

Using `main`:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/main/recipes/vanilla/recipe.yaml
```

Using a release tag:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/v0.1.6/recipes/vanilla/recipe.yaml
```

---

## Trembita Recipe Example

Using `main`:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/main/recipes/trembita/recipe.yaml
```

Using a release tag:

```txt
https://raw.githubusercontent.com/Trembita-Games/redm-txadmin-recipes/v0.1.6/recipes/trembita/recipe.yaml
```

---

## Recommended Validation

Test recipes in a clean directory before using them for a real server.

Suggested test path:

```txt
D:\Projects\RDR2\txadmin-recipe-test
```

Do not run recipe experiments directly inside an existing Git working tree unless you intentionally want txAdmin to generate files there.

---

## Recommended Data Folder Naming

txAdmin generates the `.base` folder name from the recipe metadata field:

```yaml
name: Trembita-RDR2
```

Expected generated format:

```txt
Trembita-RDR2_<txadmin-generated-suffix>.base
```

The suffix is controlled by txAdmin.

---

## Notes

Use `main` only for active testing.

Use release tags for stable deployment.
