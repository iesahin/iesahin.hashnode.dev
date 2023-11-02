---
title: "gitignore_global"
datePublished: Tue Oct 17 2023 13:11:34 GMT+0000 (Coordinated Universal Time)
cuid: clogzv0ei019to8nv8ken63kl
slug: gitignoreglobal
canonical: https://emresahin.net/gitignore-global/

---

You can configure a `.gitignore_global` file to ignore files or directories (e.g. `.vscode/`) in all your repositories. Write it as a standard `.gitignore` file and save it to some place, like `~/.gitignore_global` . Then you can use the following configuration to set this as an _excludes file._

    git config --global core.excludesfile ~/.gitignore_global
    

Note that, the path given to `git config` should be a global path.