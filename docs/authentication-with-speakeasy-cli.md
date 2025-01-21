

  # Authentication with Speakeasy CLI

The Speakeasy CLI provides a robust authentication system that allows users to securely interact with the Speakeasy Platform. The `auth` command and its subcommands manage the authentication process, enabling users to log in, log out, and switch between authenticated workspaces.

## Overview

The authentication system in Speakeasy CLI consists of the following main components:

1. `auth`: The parent command for all authentication-related operations.
2. `login`: Authenticates the CLI for use with the Speakeasy Platform.
3. `logout`: Removes authentication from the CLI.
4. `switch`: Changes the default workspace to a different authenticated workspace.

## Usage

To access authentication-related commands, use the following syntax:

```
speakeasy auth [subcommand] [flags]
```

### Available Subcommands

- `login`: Authenticate the CLI
- `logout`: Logout of the CLI
- `switch`: Switch between authenticated workspaces

### Global Options

The following option is available for all `auth` subcommands:

- `--logLevel string`: Sets the log level (available options: [info, warn, error], default: "info")

## Authentication Workflow

1. **Login**: Use `speakeasy auth login` to authenticate the CLI with the Speakeasy Platform. This command will guide you through the authentication process.

2. **Use CLI**: Once authenticated, you can use various Speakeasy CLI commands that require authentication.

3. **Switch Workspaces**: If you have multiple authenticated workspaces, use `speakeasy auth switch` to change the default workspace.

4. **Logout**: When you're done or want to remove authentication, use `speakeasy auth logout`.

## Best Practices

- Always ensure you're using the correct workspace when executing commands.
- Regularly check your authentication status, especially when working with sensitive operations.
- Log out when you're done working, especially on shared or public machines.

For more detailed information on each authentication command, refer to the specific command documentation:

- [Login](login.md)
- [Logout](logout.md)
- [Switch](switch.md)

By effectively using these authentication commands, you can securely manage your interactions with the Speakeasy Platform through the CLI.

  