---
include: "*.sh"
title: Shell script best practices
tags: shell
---

Follow these shell script best practices when writing or modifying bash scripts:

1. Use `#!/usr/bin/env bash` instead of `#!/bin/bash` for better portability

Bad:

```bash
#!/bin/bash
echo "Hello World"
```

Good:

```bash
#!/usr/bin/env bash
echo "Hello World"
```

2. Use `${variable}` syntax for all variable references

Bad:

```bash
name="Alice"
echo "Hello $name"
```

Good:

```bash
name="Alice"
echo "Hello ${name}"
```

3. Use double quotes around variable expansions to prevent word splitting and globbing

Bad:

```bash
files=$(ls)
for file in $files; do
  rm $file
done
```

Good:

```bash
files=$(ls)
for file in "${files}"; do
  rm "${file}"
done
```

4. Use `[[` and `]]` instead of `[` and `]` for conditional expressions

Bad:

```bash
if [ -z "$input" ] || [ "$input" = "exit" ]; then
  echo "Exiting..."
  exit 0
fi
```

Good:

```bash
if [[ -z "${input}" || "${input}" = "exit" ]]; then
  echo "Exiting..."
  exit 0
fi
```

5. Use `printf '%s\n'` instead of `echo` for output with special characters

Bad:

```bash
output="Text with special chars: * & $HOME"
echo $output
```

Good:

```bash
output="Text with special chars: * & $HOME"
printf '%s\n' "${output}"
```

6. Use `readonly` for constants that should not be modified

Bad:

```bash
CONFIG_PATH="/etc/app/config.json"
LOG_DIR="/var/log/app"
```

Good:

```bash
readonly CONFIG_PATH="/etc/app/config.json"
readonly LOG_DIR="/var/log/app"
```

7. Use `|` as delimiter in `sed` commands when replacing paths containing slashes

Bad:

```bash
sed -i "s/${source_path}/${target_path}/" "${config_file}"
```

Good:

```bash
sed -i "s|${source_path}|${target_path}|" "${config_file}"
```
