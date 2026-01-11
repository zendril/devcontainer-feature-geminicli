# Gemini CLI DevContainer Feature

A [DevContainer feature](https://containers.dev/implementors/features/) that installs Google's Gemini CLI, providing AI-powered assistance directly in your development container terminal.

## What is Gemini CLI?

Gemini CLI is a command-line interface that brings Google's Gemini AI model capabilities to your terminal, enabling you to interact with AI for code generation, debugging assistance, and general queries without leaving your development environment.

## Features

- Installs the latest version of `@google/gemini-cli` via npm
- Automatically includes the Google GenAI Code Assist VS Code extension
- Persistent configuration and history across container rebuilds
- Seamless integration with DevContainer workflows

## Installation

Add this feature to your `.devcontainer/devcontainer.json`:

```json
{
  "features": {
    "ghcr.io/zendril/features/gemini-cli:1": {}
  }
}
```

### With Custom Version

To install a specific version of Gemini CLI:

```json
{
  "features": {
    "ghcr.io/zendril/features/gemini-cli:1": {
      "version": "latest"
    }
  }
}
```

## Usage

After rebuilding your container, you can use the Gemini CLI directly in your terminal:

```bash
gemini "How do I fix this error?"
```

For authentication and additional configuration, refer to the [official Gemini CLI documentation](https://geminicli.com/docs/).

## Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `version` | string | `latest` | Specify the version of Gemini CLI to install |

## Dependencies

This feature automatically installs after the Node.js feature if present. If Node.js is not already in your container, it will be installed as a dependency.

## VS Code Integration

This feature includes the `Google.genai-code-assist` VS Code extension, which provides additional AI-assisted coding capabilities within your editor.

## How It Works

This feature uses [nanolayer](https://github.com/devcontainers-extra/nanolayer) to keep container layers minimal and leverages the battle-tested [devcontainers-extra npm-package feature](https://github.com/devcontainers-extra/features) for reliable npm package installation.

## Troubleshooting

### Authentication

You may need to authenticate with your Google account on first use:

```bash
gemini auth login
```

### Command Not Found

If the `gemini` command is not found after installation, try:

1. Rebuilding your container completely
2. Checking that Node.js is properly installed
3. Verifying the installation with `npm list -g @google/gemini-cli`

## Contributing

Issues and pull requests are welcome at the [GitHub repository](https://github.com/zendril/devcontainer-feature-geminicli).

## License

See [LICENSE](LICENSE) file for details.
