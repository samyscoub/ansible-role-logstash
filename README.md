# Logstash - Ansible role

 * Installs logstash from tar, deb or rpm
 * Fetchs from remote web or local copy
 * Tested on Debian Wheezy (7) and deb only
 * Should work on RedHat 6, 7 and Debian Jessie (8)


This role installs a JRE. If you dont want to do so, set `logstash_install_java: false`.

You can also change java packages with the list `logstash_packages_java`.

Configuration templates are poor right now but they will be enrich soon.

## Basic template

By default, it will generate a simple TCP listener on port 5410 (dont ask me why this one) and outputs into a local Elasticsearch server.

If you want some extra basic configuration, set these variables like this:

```yaml
logstash_(inputs|filters|outputs):
    -
      type: (input|filter|output)_name
      options:
          -
            key: option_name
            value: option_value
```

## Custom configuration files

If you dont want such a basic configuration or have conditional statements, dont use the basic template and write your own configuration files.

They should be located in a directory like `host_files/<ansible_nodename>/logstash/` and named like `myconf.conf`.

Then set `logstash_custom_conf_files` variable like this:

```yaml
logstash_custom_conf_files:
    - 'my_inputs_tcp'
    - 'my_inputs_udp'
    - 'my_filters_blafilter'
    - 'my_filters_bla2filter'
    - 'my_outputs_elasticsearch'
    - 'my_outputs_rabbitmq'
```

Then set `logstash_use_basic_template: false`. It is optional, just remember the default basic template will be named `0000_logstash.conf`
