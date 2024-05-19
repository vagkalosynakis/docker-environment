## VSCode path mappings

In order for xdebug to work in VSCode, we need to set the path mappings in `launch.json`:


```
"pathMappings": {
    "/var/www/html": "${workspaceFolder}/src"
}
```