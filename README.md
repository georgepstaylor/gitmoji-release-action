# gitmoji-release-action

This action generates releases and has options to automatically create tags and release notes based on gitmoji labels.

Note: GitHub _requires_ more than just the gitmoji in the title, so this action will create the labels
as `<gitmoji>_gitmoji` for example `✨_gitmoji` or `🐛_gitmoji` etc.

## Usage
```yaml
- name: Create Release
  uses: georgepstaylor/gitmoji-auto-label@v0.0.1
  with:
    GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
    release_type: 'patch'
    auto_create_tag: true
    title_suffix: '- Release'         
```

### Using this action to assist with GitHub automated release notes

Optionally you can use this action in conjunction with [georgepstaylor/gitmoji-auto-label](https://github.com/georgepstaylor/gitmoji-auto-label) to automatically generate releases and release notes based on the gitmoji labels.

Likewise, you can create releases using the GitHub UI and the release notes will be generated based on the gitmoji labels if you use the following configuration:

See: 
- https://docs.github.com/en/repositories/releasing-projects-on-github/automatically-generated-release-notes
- https://docs.github.com/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository

```yaml
# .github/release.yml
changelog:
  exclude:
    labels:
      - ignore-for-release
    authors:
      - octocat
  categories:
    - title: Exciting New Features and Enhancements ✨
      labels:
        - ✨_gitmoji
        - ⚡_gitmoji
        - 🚀_gitmoji
        - 🎉_gitmoji
        - 🥚_gitmoji
    - title: Security Fixes 🔒
      labels:
        - 🔒_gitmoji
        - 🛡️_gitmoji
        - 🛂_gitmoji
        - 🔐_gitmoji
    - title: Bug Fixes 🐛
      labels:
        - 🐛_gitmoji
        - 🚑_gitmoji
        - 🩹_gitmoji
    - title: Documentation 📚
      labels:
        - 📚_gitmoji
        - 📝_gitmoji
        - 💡_gitmoji
        - 📄_gitmoji
    - title: Typo Corrections 📝
      labels:
        - 📝_gitmoji
        - 📚_gitmoji
    - title: Breaking Changes 💥
      labels:
        - 💥_gitmoji
    - title: Refactor ♻️
      labels:
        - ♻️_gitmoji
        - ⚰️_gitmoji
        - 🗑️_gitmoji
        - 🚚_gitmoji
    - title: Work In Progress 🚧
      labels:
        - 🚧_gitmoji
        - 🍺_gitmoji
        - 💩_gitmoji
    - title: Dependency Updates 📦
      labels:
        - ➕_gitmoji
        - ➖_gitmoji
        - 📌_gitmoji
        - ⬆️_gitmoji
        - ⬇️_gitmoji
    - title: Other Changes
      labels:
        - "*"
```