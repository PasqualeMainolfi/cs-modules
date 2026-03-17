# Csound Community Modules

**NOTE: This repository is currently under active development and testing. A stable release will be published once the system is finalized.**  

This repository hosts a community collection of Csound modules.  
It provides a simple and transparent structure where users can publish, share, and discover reusable Csound components.  
The repository is designed to be easy to maintain and easy to consume by tools such as `cspm`, while remaining fully readable and manageable by humans.

## Repo structure

The repository is organized into two main parts (modules and projects):

```
├── csm-registry.json
└── modules
    ├── <module-name>
    │   ├── <version>
    │   │   └── <module files>
    │   └── <version>
    │       └── <module files>
    └── ...
    
├── csp-registry.json
└── projects
    ├── <project-name>
    │   ├── <project files>
    └── ...
```

### registry files

The `csm-registry.json` and `csp-registry.json` file contains the list of available modules and their published versions and projects.

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

Each entry maps a module or project name to the list of available versions, authors and description.

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

### projects/

The projects directory contains the actual project packages.

```
projects/
  project1/
    src/
        main.csd or (main.orc/main.sco)
    Cspm.toml
    <Cspm.lock> (optional)
  project2/
    src/
        main.csd or (main.orc/main.sco)
    Cspm.toml
    <Cspm.lock> (optional)
```

### Versioning

Module versions follow the `major.minor.patch` format (e.g. `1.2.0`).  
Each component must be numeric. Versions are compared numerically and do not follow semantic versioning rules.  
If a version is specified during installation, that exact version will be installed.  
If no version is specified, Cspm installs the **latest available version**. The same rule applies when updating modules.

## Publishing a module

To publish a new module or share a project to the community repository, follow these steps:

1. **Fork the Repository**: start by forking the official modules repository to your GitHub account
2. **Add Your Module/Project**: Add your package following the required repository structure.
    - **Modules**: Each version must reside in its own directory: `modules → <module-name> → <version> → <module files>`
    - **Projects**: Each project must reside in its own directory: `projects → <project-name> → <project files>`
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

4. **Open a Pull Request**: If all checks pass, create a Pull Request from your fork to the official repository. After review and approval, the module/project will be merged and made available to the community
