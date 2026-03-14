# Csound Community Modules

**NOTE: This repository is currently under active development and testing. A stable release will be published once the system is finalized.**  

This repository hosts a community collection of Csound modules.  
It provides a simple and transparent structure where users can publish, share, and discover reusable Csound components.  
The repository is designed to be easy to maintain and easy to consume by tools such as `cspm`, while remaining fully readable and manageable by humans.

## Repo structure

The repository is organized into two main parts:

```
├── cs-registry.json
└── modules
    ├── <module-name>
    │   ├── <version>
    │   │   └── <module files>
    │   └── <version>
    │       └── <module files>
    └── ...
```

### cs-registgry.json

The `registry.json` file contains the list of available modules and their published versions.

```json
{
  "module1": {
      "versions": ["0.1.0", "0.2.0", ...]
      "authors": ["author1", "author2", ...],
      "descriprion": "description of the module1"
  },
  "module2": {
      "versions": ["0.1.0", "0.2.0", ...]
      "authors": ["author1", "author2", ...],
      "descriprion": "description of the module2"
  }
}
```

Each entry maps a module name to the list of available versions.

### modules/

The modules directory contains the actual module packages.

```
modules/
  module1/
    1.0.0/
      src/
         main.udo
      Cspm.toml
      <Cspm.lock> (optional)
    1.1.0/
      src/
         main.udo
      Cspm.toml
      <Cspm.lock> (optional)
```

## Publishing a module

To publish a new module to the community repository, follow these steps:

1. **Fork the Repository**: start by forking the official modules repository to your GitHub account
2. **Add Your Mudule**: Add your package following the required repository structure. Each version must be placed inside its own folder (`modules 🡢 <module_name> 🡢 <version> 🡢 <module files>`)
3. **Validate with cspm**: run from shell 

```shell
cspm publish
```

This command will:
- Validate the module structure
- Check version consistency
- Verify manifest correctness
- Ensure no conflicts with existing packages
- Perform consistency checks before publication

If any issue is detected, the command will stop and report the error.

4. **Open a Pull Request**: If all checks pass, create a Pull Request from your fork to the official repository. After review and approval, the module will be merged and made available to the community
