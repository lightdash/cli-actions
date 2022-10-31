# Lightdash GitHub Actions templates

## Refresh your Lightdash project
> refresh.yml

Follow the [Lightdash documentation](https://docs.lightdash.com/references/syncing_your_dbt_changes) to know how you can
add this Github action to your DBT Github repo to automatically refresh your DBT changes into Lightdash.
This action is only available if
you [configured your Lightdash project to be connected to Github](https://docs.lightdash.com/get-started/setup-lightdash/get-project-lightdash-ready#next-steps-update-your-project-connection-settings)
, otherwise you can use the `deploy` option bellow.

## Deploy your Lightdash project
> deploy.yml

Follow the [Lightdash documentation](https://docs.lightdash.com/references/syncing_your_dbt_changes) to know how you can
add this Github action to your DBT Github repo to
automatically deploy your DBT changes into Lightdash.

## Create a preview Lightdash project on each pull request
> start-preview.yml
> stop-preview.yml

Follow the [Lightdash documentation](https://docs.lightdash.com/guides/cli/how-to-use-lightdash-preview#set-up-developer-previews-on-your-pull-requests) to know how you can
add this Github action to your DBT Github repo to automatically create preview projects with your pull request changes.

# Extra configuration

## Use CLI config instead of ENV vars

If you prefer to authenticate on the CLI using the `lightdash/config.yaml` file, just copy the full content of that file
into a `CLI_CONFIG` secret

and add the following step before `Lightdash CLI deploy`

```
      - name: Create config file 
        env: 
          config: ${{ secrets.CLI_CONFIG }}          
        run:  |
          mkdir -p $HOME/.config/lightdash
          echo -e "$config" > $HOME/.config/lightdash/config.yaml

```

Both options are compatible (env vars have priority) 
