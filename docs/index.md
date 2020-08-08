# Introduction

Runcobo is a general purpose framework built on Crystal.  

### Commands

```shell
runcobo [<commands>...] [<arguments>...]

  Commands:
    routes                      - Print all routes of the app.
    version                     - Print the current version of the runcobo.
    help                        - Print usage synopsis.

  Options:
    -h, --help                       Print usage synopsis.
    -v, --version                    Print the current version of the runcobo.
```

### Project Architecture

    lib/                # Library
    src/
        main.cr         # Entry file
        actions/        # Actions Directory
            ...
        assets/         # Assets Directory
        views/          # Views Directory
            layouts/    # Layouts directory
            ...
        models/         # Models Directory
            ...
    shards.yml          # The packages congfiuration file
    shards.lock         # The lock file for packages congfiuration file

### Design Architecture
MVC (Model-View-Controller)

### Design Principles

+ Simple Design must be simple, both in implementation and interface.
+ Intuitive Design must be intuitive.
+ Consistent Design must be consistent.