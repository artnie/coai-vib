<h1 align=center>CoAI Interactive Research Space | <a href="https://intel4coro.github.io/coai-vib/" rel="nofollow">Live Demo</a></h1>

Interactive Research Space pages built with markdown files powered by site generator [Hugo](https://gohugo.io/).
> This site is based on hugo theme [beautifulhugo](https://github.com/halogenica/beautifulhugo).

## Installation

### 1. Init git submodule to add hugo theme

    git submodule init
    git submodule update 

### 2. Install and run Hugo

#### Option 1: Install Hugo

* See [the Hugo documentation](https://gohugo.io/installation/) for details.
* Run command:

```bash
hugo server
```

#### Option 2: Start with docker

* Install Docker, See [Install Docker Engine](https://docs.docker.com/engine/install/) for details.

* Run command:

```bash
docker compose up
```

## Site preview

Open http://localhost:1313/coai-vib/

## Add/Edit Pages

Page contents are store in directory [content/posts](content/posts). To add a new page, just create folder under this directory with a markdown file named "index.md". The file "index.md" should content the following metadata:

```
---
title: "Main title"
date: 2023-10-03T10:35:35-05:00
subtitle: "Subtitle"
tags: ["Research"]
dropCap: false
displayInMenu: false
displayInList: true
draft: false
---

# Markdown Content will display in the list preview.

<!--more-->

# Markdown Content only display in detail page.
```

> Example can be found in [content/examples](content/examples) for more details.

### Display Options and Buttons

![Options and Buttons Screenshot](static/img/widget.png)

To display the above UI widgets, you need to provide a json file as resource in the "index.md" metadata:

```
---
...

resources:
- name: ActionButtons
  src: "buttons.json"
...
---
```

```json
{
  "options": {
    "{{Option Label}}": [
      {
        "name": "Household",
        "value": "household",
        "img": "./images/household.png",
        "knowledge_bases": "knowledge_bases": "{{OpenEASE Url}}"
      },
      ...
    ],
    "robots": [
      {
        "name": "PR2",
        "value": "pr2",
        "img": "{{Image url}}",
        "knowledge_bases": "{{OpenEASE Url}}"
      },
      ...
    ],
    ...
  },
  "actions": [
    {
      "name": "{{Button Label}}",
      "value": "run",
      "description": "Run code on Binderhub.",
      "primary": true,
      "url": "https://binder.intel4coro.de/v2/gh/IntEL4CoRo/COAI/master?urlpath=lab%2Ftree%2Fnotebooks%2F",
      // If the button url depends on the dropdown select boxs define above
      "options": [
        "environments",
        "robots",
        "tasks"
      ],
      // Define available options
      "available": {
        "environments=apartment|robots=tiago|tasks=setting_table": "apartment_tiago.ipynb",
        "environments=apartment|robots=pr2|tasks=setting_table": "apartment_pr2.ipynb",
        "environments=household|robots=donbot|tasks=setting_table": "household_donbot_setting_table.ipynb",
        "environments=household|robots=pr2|tasks=setting_table": "household_pr2_setting_table.ipynb",
        "environments=household|robots=tiago|tasks=setting_table": "household_tiago_setting_table.ipynb",
        "environments=household|robots=pr2|tasks=popcorn": "https://binder.intel4coro.de/v2/gh/IntEL4CoRo/cram_teaching/legacy?urlpath=lab%2Ftree%2Flectures%2Fdemos%2Fpopcorn.ipynb"
      }
    },
    // Minimium button config
    {
      "name": "Github",
      "value": "github",
      "description": "Source code",
      "url": "https://github.com/",
    }
  ]
}
```

> Example: [button.json](content/posts/Researcher's%20workbench%20for%20Household%20Robotics/buttons.json)

> Note: Currently the widget can not be previewed under development environment, should be fixed in the future.

## Development

To modify the HTML templates under directory [layouts](layouts), please read the [Hugo Documentation](https://gohugo.io/documentation/).

### Extra shortcodes

There are two extra shortcodes provided (along with the customized figure shortcode):

#### Details

This simply adds the html5 detail attribute, supported on all *modern* browsers. Use it like this:

```
{{< details "This is the details title (click to expand)" >}}
This is the content (hidden until clicked).
{{< /details >}}
```

#### Split

This adds a two column side-by-side environment (will turn into 1 col for narrow devices):

```
{{< columns >}}
This is column 1.
{{< column >}}
This is column 2.
{{< endcolumns >}}
```

### Social Media Icons

In order to show social media icons in the footer, add a section like this to your `config.yaml`.  You can see the full list of supported social media sites in `data/beautifulhugo/social.toml`.

```yaml
author: 
  name: "Author Name"
  website: "https://example.com"
  github: halogenica/beautifulhugo
  twitter: username
  discord: 96VAXXvjCB
```

## Helpful Links

[Hugo Documentation](https://gohugo.io/documentation/) - Learn how to use Hugo

[Beautiful Hugo Theme](https://github.com/halogenica/beautifulhugo) - Overwrite theme

[Markdown Cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) - Write in markdown like a pro

[Latex Math Documentation](https://en.wikibooks.org/wiki/LaTeX/Mathematics) - Learn math typesetting with LaTeX (powered by KaTeX)

## License

MIT Licensed, see [LICENSE](https://github.com/halogenica/Hugo-BeautifulHugo/blob/master/LICENSE).
