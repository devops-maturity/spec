# hugo DevOps Maturity theme
Copy hugo-devops-maturity-theme inside your my-hugo-site/theme

## config.yaml example
All config params are optionals.
```yaml
baseURL: 'https://devops-maturity.github.io/'
languageCode: en-us
title: DevOps Maturity
theme: devops-maturity

# Language
defaultContentLanguageInSubdir: true
defaultContentLanguage: "en"
languages:
  en:
    weight: 1
    languageName: "English"

# Content
params:
  versions:
    current: 1.0.0

  welcome:
    description: A specification made for write standardized and useful commit messages
    image: 'https://path-to-image'
    actions:
    - label: Read the specs
      url: 'https://github.com/devops-maturity/devops-maturity'
    - label: GitHub
      url: 'https://github.com/devops-maturity/devops-maturity'

  license:
    title: License
    action:
      label: Creative Commons - CC BY 3.0
      url: 'https://creativecommons.org/licenses/by/3.0/'

  footer:
    logos:
    - name: github
      url: 'https://github.com/devops-maturity/devops-maturity'
```

## Apply theme changes
Development script
```ssh
npm run start
```

Production script
```ssh
npm run build
```

## Shortcodes
* banner-image
  * src (optional) | default: static/img/git-flow.png