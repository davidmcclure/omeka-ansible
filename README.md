# Omeka Ansible

A simple, no-frills [Ansible][ansible] role for deploying [Omeka][omeka] from source:

- Creates the directory structure for Omeka.
- Clones the source code from GitHub.
- Sets environment-specific config files - `.htaccess`, `config.ini`, `db.ini`.
- Symlinks the `/files` directory from an external location (optional).
- Sets permissions on `/files`.
- Installs Imagemagick.
- Installs plugins and themes.

## Variables

```yaml
# The Omeka git repository and branch.

omeka_repo: https://github.com/omeka/Omeka
omeka_branch: stable-2.3

# The location of the deployed Omeka source code.

omeka_src: /var/www/html/omeka

# Database connection parameters for db.ini.

omeka_host: localhost
omeka_username: omeka
omeka_password: omeka
omeka_dbname: omeka
omeka_prefix: omeka_
omeka_charset: utf8
omeka_port: 3306

# A list of themes to install.

omeka_themes:

  - name: neatlight
    repo: https://github.com/davidmcclure/neatlight.git
    version: master

# A list of plugins to install.

omeka_plugins:

  - name: Neatline
    repo: https://github.com/scholarslab/Neatline.git
    version: 2.3.0

  - name: NeatlineText
    repo: https://github.com/scholarslab/nl-widget-Text.git
    version: v1.0.1

# If `omeka_files` is defined, the playbook will symlink an external /files
# directory from elsewhere on the file system. Eg, an attached EBS volume.

# omeka_files: /path/to/files
```

## Contributing

If you find bugs, file an issue or send a PR! Or, hit me up on [Twitter][clured].

[ansible]: http://www.ansible.com
[omeka]: http://omeka.org
[clured]: https://twitter.com/clured
