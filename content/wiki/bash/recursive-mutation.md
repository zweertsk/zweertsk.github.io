+++
title = 'Recursive Mutation'
date = 2023-11-01T17:02:51+01:00
draft = true
wikis = ['Bash']
+++
For each file, make a directory with title from file and move the file in that new directory.

```bash
for f in *.*; do [ -f "$f" ] || continue; mkdir "${f%.*}" && mv "$f" "${f%.*}"; done
```
