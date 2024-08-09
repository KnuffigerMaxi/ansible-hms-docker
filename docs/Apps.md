# Automatic App Initialization

By default, the playbook will check for the various apps API keys in their config files in order to update the `.env` file so there is a seamless integration with the Homepage app (for most apps).

If you set `hmsdocker_init_apps` to `yes` in `inventory/group_vars/all/main_custom.yml`, it will also attempt to connect some of the apps together to speed up initial installation process. It will automatically wait for 1min to ensure containers have fully started and created their config files.

NOTE: This will only _create_ the connections if they do not exist already, it will not update existing connections. These connections are prefixed with `HMSD - ` and this is required to work correctly. You can modify the settings of the connection, but not the name.

It will:

* Configure the Sonarr and Radarr apps (including 4K instances if enabled) in Prowlarr

* Configure FlareSolverr and Tranmission Indexer Proxies in Prowlarr

* Configure app-level Transmission proxy for Prowlarr, Sonarr(s), Radarr(s)

* Configure Transmission as a download client in Sonarr(s) and Radarr(s)
