# Templates

Configuration templates used by txAdmin recipes.

---

## Structure

```txt
templates/
├── vanilla/
│   ├── server.cfg
│   └── permissions.cfg
└── vanilla-with-server-data/
    ├── server.cfg
    └── permissions.cfg
```

---

## Purpose

Templates keep recipe YAML files smaller and easier to read.

They also make server configuration easier to review separately from deployment logic.

---

## Notes

Templates are intended for txAdmin recipe generation.

They are not the same as the Git-first configuration files in `redm-vanilla-template`.