# GUIDELINES

## How do I move plugins here?

### Workflow

1. Submit a PR to the [infrastructure](https://github.com/rm3l/asdf-community-infrastructure/blob/main/terraform/github/teams.tf) repository to add a team as follows:

   ```hcl
   <PLUGIN NAME> = {
     description = "The people with push access to the <PLUGIN NAME> repository"
     maintainers = [
       "<GITHUB USERNAME>",
     ]
   }
   ```

2. Once the PR is merged, you will be invited to the organisation and then transfer the repository to the organisation.

3. Submit a PR to the [infrastructure](https://github.com/rm3l/asdf-community-infrastructure/blob/main/terraform/github/repositories.tf) repository to put the repository under Terraform control.

   > **Note** A dedicated team for the plugin must always be at the top of the team list because the top one will be written to the `CODEOWNERS` file.

   ```hcl
   <PLUGIN NAME> = {
     description    = "<TOOL NAME> for the asdf version manager"
     homepage_url   = "https://github.com/asdf-vm/asdf"
     default_branch = "main"
     topics = [
       "asdf-plugin",
       "asdf",
     ]
     teams = [
       "<PLUGIN NAME>",
       "asdf-core",
     ]
   }
   ```
