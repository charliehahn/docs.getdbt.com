---
title: Installing the dbt Cloud CLI (Alpha)
id: cloud-cli-installation
description: "Instructions for installing and configuring dbt Cloud CLI"
---

:::warning Alpha functionality 

The following installation instructions are for the dbt Cloud CLI, currently in alpha. These instructions are not intended for general audiences at this time. 

::: 

## Installing dbt Cloud CLI

### Install and update with Brew on MacOS (recommended)

Install the CLI: 

```bash
brew tap dbt-labs/dbt-cli
brew install dbt-cloud-cli
```

Verify the installation:

```bash
which dbt
dbt --help
```

#### Upgrade the CLI with Brew

```bash
brew update
brew upgrade dbt-cloud-cli
```

### Manually install (Windows and Linux)

1. Download the latest release for your platform from [Github](https://github.com/dbt-labs/dbt-cli/releases).
2. Add the `dbt` executable to your path.
3. Move to a directory with a dbt project, and create a `dbt_cloud.yml` file containing your `project-id` from dbt Cloud.
4. Invoke `dbt --help` from your terminal to see a list of supported commands.

#### Updating dbt Cloud installation (Windows + Linux)

Follow the same process in [Installing dbt Cloud CLI](#manually-install-windows-only) and replace the existing `dbt` executable with the new one. You should not have to go through the security steps again.

## Setting up the CLI

1. Ensure that you have created a project in [dbt Cloud](https://cloud.getdbt.com/).

2. Ensure that your personal [development credentials](https://cloud.getdbt.com/settings/profile/credentials) are set on the project.

3. Create an environment variable with your [dbt cloud API key](https://cloud.getdbt.com/settings/profile#api-access):

```bash

   > $ vi ~/.zshrc

   ...

   # dbt Cloud CLI
    export DBT_CLOUD_API_KEY="1234"
   
```

4. Load the new environment variable. Note: you may need to reactivate your python virtual environment after sourcing your shell's dot file. Alternatively, restart your shell instead of sourcing the shell's dot file

```bash
   > $ source ~/.zshrc
```

5. Navigate to a dbt project

```bash
   > $ cd ~/dbt-projects/jaffle_shop
```

6. Ensure that a `dbt_cloud.yml` file exists in the project directory. The file is required to have a `project-id` field with a valid [project ID](#glossary):
You can find your project ID by selecting your project and clicking on **documentation** in the navigation bar. Your project ID is the number in the URL: https://cloud.getdbt.com/documentation/1/projects/{project id}.
```bash
> $ pwd
/Users/user/dbt-projects/jaffle_shop

> $ cat dbt_cloud.yml
project-id: '123456'
```

7. The following commands are supported as of now (we will be adding more in the future):

- `dbt run`
- `dbt build`
- `dbt deps`
- `dbt cancel`
- `dbt reattach`
- `dbt --help`

## Using dbt Cloud CLI

**Coming soon**

### Glossary

- **dbt cloud API key:** your API key found by navigating to the **gear icon**, clicking **Profile Settings**, and scrolling down to **API**.
- **Project ID:** the ID of the dbt project you're working with. Can be retrieved from the dbt cloud URL after a project has been selected, for example, `https://cloud.getdbt.com/deploy/{accountID}/projects/{projectID}`
- **Development credentials:** your personal warehouse credentials for the project you’re working with. They can be set by selecting the project and entering them in dbt Cloud. Navigate to the **gear icon**, click **Profile Settings**, and click **Credentials** from the left-side menu.
