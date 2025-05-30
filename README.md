# Hugo-admonitions

A lightweight Hugo module that adds beautiful and customizable admonition blocks to your content.

Inspiration from [mdbook-admonish](https://tommilligan.github.io/mdbook-admonish/).

> [!IMPORTANT]
> The minimum required Hugo version is `0.140.0`. If you find that features work correctly locally but not on your deployed GitHub Pages site (e.g., admonition colors are wrong), the most likely reason is that the `HUGO_VERSION` specified in your GitHub Actions workflow file (usually under `.github/workflows/`) is lower than `0.140.0`.

## Table of Contents

- [Hugo-admonitions](#hugo-admonitions)
  - [Table of Contents](#table-of-contents)
  - [Features ✨](#features-)
  - [Overview of all admonitions](#overview-of-all-admonitions)
    - [Light Mode](#light-mode)
    - [Dark Mode](#dark-mode)
    - [Header Only Mode](#header-only-mode)
  - [Installation](#installation)
    - [Hugo Module](#hugo-module)
    - [Git Clone](#git-clone)
  - [Usage](#usage)
  - [Customization](#customization)
    - [Admonition Colors](#admonition-colors)
    - [Dark Mode Support](#dark-mode-support)
  - [Contributing](#contributing)
  - [License](#license)

## Features ✨

- Various beautiful and simple callout available 🎨
- Blockquote style 💬
  - Portable Markdown style (GitHub, Obsidian, Typora, etc.) 📝

  - ```md
    > [!WARNING]
    > Warning: This operation will delete all data.
    ```

- Dark mode support 🌙
- Header Only Mode 📑
- Multi-language support 🌐
  - English
  - Chinese
  - French
  - German
  - Swahili
  - [Localization PRs are always welcome!](https://github.com/KKKZOZ/hugo-admonitions/pulls)

## Overview of all admonitions

### Light Mode

![light-callout](docs/assets/images/light-callout.png)

### Dark Mode

![dark-callout](docs/assets/images/dark-callout.png)

### Header Only Mode

<div align="center">
  <img src="docs/assets/images/header-only-mode.png" width="500" alt="header-only-mode">
</div>

## Installation

> [!IMPORTANT]
> This modules requires Hugo `v0.140.0` or later.

### Hugo Module

1. Install the [Go programming language](https://go.dev/doc/install).

2. Initialize your own hugo module:

    ```shell
    hugo mod init YOUR_OWN_GIT_REPOSITORY
    ```

3. Add `hugo-admonitions` in your site's configuration file:

    With `hugo.yaml`:

    ```yaml
    module:
      imports:
        - path: github.com/KKKZOZ/hugo-admonitions
        - path: my-theme
    ```

    With `hugo.toml`:

    ```toml
    [module]
      [[module.imports]]
        path = "github.com/KKKZOZ/hugo-admonitions"
      [[module.imports]]
        path = "my-theme"
    ```

4. Finally update by running:

    ```shell
    hugo mod get -u
    ```

### Git Clone

1. Inside the folder of your Hugo site, run:

    ```bash
    git clone git@github.com:KKKZOZ/hugo-admonitions.git themes/hugo-admonitions --depth=1
    ```

2. Add `hugo-admonitions` as the left-most element of the theme list variable in your site's or theme's configuration file `hugo.yaml` or `hugo.toml`.

    With `hugo.yaml`:

    ```yaml
    theme: ["hugo-admonitions", "my-theme"]
    ```

    With `hugo.toml`:

    ```toml
    theme = ["hugo-admonitions", "my-theme"]
    ```

## Usage

See [demo.md](docs/content/demo.md) for examples.

Use the blockquote in this way:

```markdown
> [!NOTIFY]
> System notification: Your password will expire in 30 days.
```

![usage-1](docs/assets/images/usage-1.png)

<details>
<summary>Available Callouts List</summary>

- `[!ABSTRACT]`
- `[!CAUTION]`
- `[!CODE]`
- `[!CONCLUSION]`
- `[!DANGER]`
- `[!ERROR]`
- `[!EXAMPLE]`
- `[!EXPERIMENT]`
- `[!GOAL]`
- `[!IDEA]`
- `[!IMPORTANT]`
- `[!INFO]`
- `[!MEMO]`
- `[!NOTE]`
- `[!NOTIFY]`
- `[!QUESTION]`
- `[!QUOTE]`
- `[!SUCCESS]`
- `[!TASK]`
- `[!TIP]`
- `[!WARNING]`

</details>

<br/>

> [!NOTE]
> Unsupported callout types will default to `[!NOTE]`

Or you can customize the title by using any of them:

```markdown
> [!IDEA] Summary
> This is a summary using the `IDEA` callout!
```

![usage-2](docs/assets/images/usage-2.png)

```markdown
> [!MEMO] Summary
> This is a summary using the `MEMO` callout!
```

![usage-3](docs/assets/images/usage-3.png)

Use the Header Only mode by including a title only:

```markdown
> [!TIP] You can choose to only to show the header!

> [!NOTIFY] System notification: Your password will expire in 30 days

> [!SUCCESS] Congratulations! Your code has been successfully deployed to production

> [!WARNING] Warning: This operation will delete all data. 
```

![usage-4](docs/assets/images/usage-4.png)

## Customization

Please follow the instructions below to override the default styles.

1. Create a new Sass file.

    Run these commands from the root of your project:

    ```shell
    mkdir -p assets/sass/vendors
    touch assets/sass/vendors/_admonitions.scss
    ```

    The resulting directory structure will look like this:

    ```text
    your-hugo-project/
    └── assets/
        └── sass/
            └── vendors/
                └── _admonitions.scss
    ```

2. Copy the contents of the [source file] into the file you created.
3. Update the styles as needed.

### Admonition Colors

The colors can easily updated by changing the first part of the file

> With clear comments!

```scss
// --- Theme Colors ---
// Define the colors used for admonition elements in both light and dark modes.

// Light Mode Colors
$admonition-light-bg: #ffffff !default; // Content background
$admonition-light-text: #000000 !default; // Content text
$admonition-light-code-bg: #f5f5f5 !default; // Inline code & code block background
$admonition-light-code-text: #24292e !default; // Inline code & code block text
$admonition-light-blockquote-border: #e0e0e0 !default; // Blockquote left border

// Dark Mode Colors
$admonition-dark-bg: #1d1e20 !default; // Content background
$admonition-dark-text: #e6e6e6 !default; // Content text
$admonition-dark-code-bg: #313244 !default; // Inline code & code block background
$admonition-dark-code-text: #cdd6f4 !default; // Inline code & code block text
$admonition-dark-blockquote-border: #45475a !default; // Blockquote left border

// --- Header Background Opacity ---
// Controls the opacity of the background color tint in the header.
// Value should be between 0 (transparent) and 1 (opaque).
$admonition-light-header-bg-opacity: 0.1 !default; // Opacity for light mode header background
$admonition-dark-header-bg-opacity: 0.1 !default; // Opacity for dark mode header background (can be same or different)
```

### Dark Mode Support

By default, `hugo-admonitions` attempts to automatically detect and apply dark mode styling to match your website's theme.

**How it Works:**

Instead of relying on the operating system's preference (`prefers-color-scheme`), this module checks for the presence of specific CSS selectors on your `<html>` or `<body>` tags. The default configuration looks for a wide range of common selectors used by popular Hugo themes and CSS frameworks:

- `html[data-theme="dark"]`, `body[data-theme="dark"]`
- `html[data-bs-theme="dark"]`
- `html[data-scheme="dark"]`, `body[data-scheme="dark"]`
- `html[data-color-mode="dark"]`, `body[data-color-mode="dark"]`
- `body.dark`, `body.dark-mode`, `body.theme-dark`
- `html.dark`, `html.dark-mode`

This list is defined by the `$admonition-dark-selector` variable within the module's SCSS file.

**When Customization is Needed:**

If your theme uses a *different* CSS class or data attribute not included in the default list above, the admonition blocks might remain in light mode even when your site switches to dark mode.

**How to Customize the Dark Mode Trigger:**

You can easily tell `hugo-admonitions` which selector(s) your theme uses by overriding the `$admonition-dark-selector` SCSS variable.

> [!NOTE]
> If you encounter difficulties getting dark mode to work correctly with your specific theme, even after following these steps, or if anything in this guide is unclear, please don't hesitate to **open an [issue](https://github.com/KKKZOZ/hugo-admonitions/issues/new)**!

[source file]: https://github.com/KKKZOZ/hugo-admonitions/blob/main/assets/sass/vendors/_admonitions.scss

## Contributing

Contributions are welcome! Please feel free to submit a [Pull Request](https://github.com/KKKZOZ/hugo-admonitions/pulls).

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
