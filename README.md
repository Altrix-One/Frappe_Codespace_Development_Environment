<div align="center">
    <h2>Frappe Development Environment</h2>
</div>

## Usage

To use in either production or development environments with the default or custom Frappe Framework, you can edit the `installer.py` file:

- **-r (or --frappe-repo)**: Specifies the URL of the Frappe repository to use, with a default value of `https://github.com/frappe/frappe.git`.
- **-t (or --frappe-branch)**: Specifies the branch of the Frappe repository to use, with a default value of `version-15`.

## Custom Framework and Environment Setup

To choose a custom framework or switch between a development codespace and a production environment, edit the following lines in `installer.py`:

- **Line 74**: Determines the framework repo to use.
- **Line 75**: Specifies the branch to use.
- **Line 82 and 83**: For default branches.

Example:
```python
parser.add_argument(
    "-r",
    "--frappe-repo",
    action="store",
    type=str,
    help="Frappe repo to use, default: https://github.com/frappe/frappe.git",
    default="https://github.com/frappe/frappe.git",
)
parser.add_argument(
    "-t",
    "--frappe-branch",
    action="store",
    type=str,
    help="Frappe branch to use, default: version-15",
    default="version-15",
)
```

## Choosing Modules to Install

To choose what modules to install, modify the `create_site_in_bench` function:

```python
def create_site_in_bench(args):
    if target_branch == "":
        target_branch = default_branch
    # Add the apps to install
    apps_to_get = [
        ("erpnext", "https://github.com/frappe/erpnext.git", target_branch),
    ]
```

## Using Codespaces

You can use GitHub Codespaces to develop in this environment directly from your browser or in Visual Studio Code.

### Using Codespaces in the Browser

1. Navigate to the repository on GitHub.
2. Click on the `Code` button.
3. Select `Open with Codespaces`.
4. If you don't have a Codespace created already, click on `New codespace`.

### Using Codespaces in Visual Studio Code

1. Ensure you have the [GitHub Codespaces extension](https://marketplace.visualstudio.com/items?itemName=GitHub.codespaces) installed in Visual Studio Code.
2. Navigate to the repository on GitHub.
3. Click on the `Code` button.
4. Select `Open with Codespaces` and choose to open it in Visual Studio Code.
5. Alternatively, you can open Visual Studio Code, click on the `Remote Explorer` icon in the Activity Bar, and connect to your Codespace from there.

This allows you to seamlessly develop and test your Frappe applications in a consistent environment across different devices.

Final step will allways be: "cd /frappe-bench" so that you can run bench commands.

Tips - 
Bench Build + Bench Migrate is your best friend when making changes.

Bench get-app (app link or name) to pull and app
Bench --site development.localhost install-app (app_name)



