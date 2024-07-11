---
title: Navigation 
Metadata can be used for tracking
author:
date created:
date approved:

---

# The Top Menus

In the "material" theme, the top menus are determined by settings in the "mkdocs.ylm" configuration file.

``` py
site_name: Smile4yourself Testing Web
theme:
  name: material # or redthedocs
  features:
    - navigation.tabs
    - navigation.top
    - search.suggest
    - seach.highlight
    - content.tabs.link
    - content.code.annotation
    - content.code.copy  

  language: en
  palette:
  - scheme: default
    toggle:
      icon: material/toggle-switch-off-outline
      name: Switch to dark made
    primary: teal
    accent: purple
  - scheme: slate
    toggle:
      icon: material/toggle-switch
      name: switch to light mode
    primary:  teal
    accent: lime

nav:
  - Home: index.md
  - Website:  invoke_web.md
  - Top Menu: top_menu.md
  - Docs:
    - Introduction: file1.md
    - TomTom: file4.md
    - Mummy: file45.md
    - file45: file45.md
  - Blog: blog.md
  - Contact: index.md
  - More: index.md
  - 8: index.md

extra_css:
    - css/custom.css
    

```