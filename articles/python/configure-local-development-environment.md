---
title: Configure your local Python environment for Azure development
description: How to set up a local Python dev environment for working with Azure.
ms.date: 03/01/2022
ms.topic: conceptual
ms.custom: devx-track-python
---

# Configure your local Python dev environment for Azure

To develop Python applications using Azure, you first want to configure your local development environment.  This includes creating an Azure account, installing tools for Azure development, and connecting those tools to your Azure account.

Developing on Azure requires Python 3.6 or higher. It's assumed you already have Python 3.6 or higher installed on your local workstation. To verify the version of Python on your workstation, type the command `python3 --version` in any console window.

## Create an Azure Account

To develop Python applications with Azure, you need an Azure account.  Your Azure account is the credentials you use to sign-in to Azure with and what you use to create Azure resources.

If you're using Azure at work, talk to your company's cloud administrator to get your credentials used to sign-in to Azure.

Otherwise, you can create an [Azure account for free](https://azure.microsoft.com/free/python/) and receive 12 months of popular services for free and a $200 credit to explore Azure for 30 days.

> [!div class="nextstepaction"]
> [Create an Azure account for free](https://azure.microsoft.com/free/python/)

## Sign in to Azure

Once you have your credentials, sign in to the [Azure portal](https://portal.azure.com) at https://portal.azure.com. It's recommended that to bookmark the Azure portal (https://portal.azure.com) for ease of reference in the future.

> [!div class="nextstepaction"]
> [Sign in to the Azure portal](https://portal.azure.com)

## Install Azure Tools extension for VS Code

You can use any editor or IDE to write Python code when developing for Azure.  For developers using VS Code, you'll want to install the [Azure Tools extension pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack).  The Azure Tools extension pack contains extensions for working with Azure App Service, Azure Functions, Azure Storage, Cosmos DB, and Azure Virtual Machines in one convenient package.

To install the extension from Visual Studio Code:

1. Press <kbd>Ctrl+Shift+X</kbd> to open the **Extensions** window.
1. Search for the *Azure Tools* extension.
1. Select the **Install** button.

:::image type="content" source="./media/configure-local-development-environment/vs-code-azure-tools-install-small.png" alt-text="Screenshot of the Visual Studio Code showing extensions panel searching for the Azure Tools extension pack." lightbox="./media/configure-local-development-environment/vs-code-azure-tools-install.png":::

To learn more about installing extensions in Visual Studio Code, refer to the [Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery) document on the Visual Studio Code website.

### Sign-in to your Azure account with Azure Tools

On the left-hand panel, you'll see an Azure icon. Select this icon, and a control panel for Azure services will appear. Choose **Sign in to Azure...** under any service to complete the authentication process for the Azure tools in Visual Studio Code.

:::image type="content" source="./media/configure-local-development-environment/vs-code-azure-login-small.png" alt-text="Screenshot of the Visual Studio Code showing how to sign-in the Azure tools to Azure." lightbox="./media/configure-local-development-environment/vs-code-azure-login.png":::

## Install the Azure CLI

In addition to the Azure portal, Azure also offers the [Azure CLI](/cli/azure/) command-line tool to create and manage Azure resources. The Azure CLI offers the benefits of efficiency, repeatability, and the ability to script recurring tasks. In practice, most developers use both the Azure portal and the Azure CLI.

### [Install on macOS](#tab/macOS)

The Azure CLI is installed through homebrew on macOS. If you don't have homebrew available on your system, [install homebrew](https://docs.brew.sh/Installation.html) before continuing.

```bash
brew update && brew install azure-cli
```

This command will first update your brew repository information and then install the Azure CLI.

### [Install on Linux](#tab/linux)

[!INCLUDE [Azure CLI Install Linux](includes/azure-cli-install-linux.md)]

### [Install on Windows](#tab/windows)

Download and install the latest release of the Azure CLI for Windows.

> [!div class="nextstepaction"]
> [Download the Azure CLI for Windows](https://aka.ms/installazurecliwindows)

---

After installing, sign-in to your Azure account from the Azure CLI by typing the command `az login` in a terminal window on your workstation.

```azurecli
az login
```

The Azure CLI will open your default browser to complete the sign-in process.

## Configure Python virtual environments

When creating Python applications for Azure, it's recommended to create a [virtual environment](https://docs.python.org/3/tutorial/venv.html) for each application. A virtual environment is a self-contained directory for a particular version of Python plus the additional packages needed for that application.

To create a virtual environment, follow these steps.

1. Open a terminal or command prompt.

1. Create a folder for your project.

1. Create the virtual environment:

    ### [macOS/Linux](#tab/bash)

    ```bash
    python3 -m venv .venv
    ```

    ### [Windows](#tab/cmd)

    ```bash
    # py -3 uses the global python interpreter. You can also use python3 -m venv .venv.
    py -3 -m venv .venv
    ```

    ---

    This command runs the Python `venv` module and creates a virtual environment in a folder named `.venv`.

1. Activate the virtual environment:

    ### [macOS/Linux](#tab/bash)

    ```bash
    source .venv/bin/activate
    ```
    
    ### [Windows](#tab/cmd)

    ```cmd
    .venv\scripts\activate
    ```

    ---

Once you activate that environment (which Visual Studio Code does automatically), running `pip install` installs a library into that environment only. Python code running in a virtual environment will use the specific package versions installed into that virtual environment. This allows different applications to use different versions of a package, which is sometimes required.

## Next step

> [!div class="nextstepaction"]
> [Provisioning, accessing, and managing resources >>>](cloud-development-provisioning.md)
