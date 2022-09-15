# Check bumpversion Config Action

This action checks your `.bumpversion.cfg` contains a `current_version` key and a `new_version` key which is set to a later version.

# Example usage

```yaml
uses: landtechnologies/actions-check-bumpversion-cfg@v2.0.0
```

Enforces that you have a `.bumpversion.cfg` like
```cfg
[bumpversion]
current_version = 1.0.0
new_version = 1.0.1

[bumpversion:part:auto]
```

Example configs which would fail this check

Missing `new_version`
```cfg
[bumpversion]
current_version = 1.0.0

[bumpversion:part:auto]
```

Missing `current_version`
```cfg
[bumpversion]
new_version = 1.0.0

[bumpversion:part:auto]
```

`new_version < current_version`
```cfg
[bumpversion]
current_version = 3.0.0
new_version = 2.1.0

[bumpversion:part:auto]
```

`new_version` == `current_version`
```cfg
[bumpversion]
current_version = 3.0.0
new_version = 3.0.0

[bumpversion:part:auto]
```

Missing `bumpversion:part:auto` section
```cfg
[bumpversion]
current_version = 3.0.0
new_version = 4.0.0
```
