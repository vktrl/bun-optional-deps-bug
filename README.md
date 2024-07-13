### Bun installing optional deps when it shouldn't

`bunfig.toml`:

```
[install]
optional = false
```

`package.json`:

```
{
  "optionalDependencies": {
    "tunnel-ssh": "5.1.1"
  }
}
```

`tunnel-ssh/package.json`:

```
{
  "dependencies": {
    "ssh2": "^1.14.0"
  }
}
```

`ssh2/package.json`:

```
{
  "optionalDependencies": {
    "cpu-features": "~0.0.9",
  }
}
```

Resulting install:

```diff
$ bun install --dry-run
bun install v1.1.18 (5a0b9352)
 ...
 tunnel-ssh@5.1.1
 ssh2@1.15.0
 cpu-features@0.0.10
 ...
```

macOS Sonoma 14.5 M2 Pro
