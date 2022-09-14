# Automatically deploy Lightdash projects

Follow the [lightdash documentation](#TODO) to know how you can add this Github action to your DBT Github repo to automatically deploy your DBT changes into Lightdash


## Use CLI config instead of ENV vars

If you prefer to authenticate on the CLI using the `lightdash/config.yaml` file, just copy the full content of that file into a `CLI_CONFIG` secret

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
