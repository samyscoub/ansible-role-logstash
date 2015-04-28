# Logstash - Ansible role

 * Installs logstash from tar, deb or rpm
 * Fetchs from remote web or local copy
 * Tested on Debian Wheezy (7) and deb only
 * Should work on RedHat 6, 7 and Debian Jessie (8)


This role installs a JRE. If you dont want to do so, set `logstash_install_java: false`.

You can also change java packages with the list `logstash_packages_java`.

Configuration templates are poor right now but they will be enrich soon.
