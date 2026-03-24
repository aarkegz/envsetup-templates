# envsetup-templates

Configuration templates for [envsetup](https://github.com/aarkegz/envsetup).

## Supported Tools

| Tool | Description | Configuration |
|------|-------------|---------------|
| git | Version control | .gitconfig (user, email, branch) |
| zsh | Shell with antigen | .zshrc (theme, plugins) |
| vim | Editor with vim-plug | .vimrc (theme, settings) |
| neovim | Modern editor with lazy.nvim | init.lua (theme, LSP) |
| tmux | Terminal multiplexer | .tmux.conf (prefix, mouse) |
| nvm | Node.js version manager | Official script |
| rustup | Rust toolchain installer | Official script |

## Usage

```bash
# Use with envsetup
envsetup install --tools git,zsh,neovim

# Or specify this repository
envsetup update --template-url https://github.com/aarkegz/envsetup-templates
```

## Template Structure

```
envsetup-templates/
├── manifest.toml          # Repository manifest
└── tools/
    └── <tool-name>/
        ├── config.toml    # Tool configuration
        └── files/         # Template files (Tera format)
```

## Customization

1. Fork this repository
2. Modify templates in `tools/<tool-name>/files/`
3. Adjust options in `tools/<tool-name>/config.toml`
4. Use with envsetup: `envsetup --template-path /path/to/your/templates`

## Template Syntax

Templates use [Tera](https://tera.netlify.app/) syntax (similar to Jinja2):

```jinja
[user]
    name = {{ config.user_name | default(value="User") }}
    email = {{ config.user_email | default(value="user@example.com") }}
```

Variables come from user selections during the interactive wizard.

## License

MIT