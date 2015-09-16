# Ansible Role: Logstash Forwarder

[![Build Status](https://travis-ci.org/geerlingguy/ansible-role-logstash-forwarder.svg?branch=master)](https://travis-ci.org/geerlingguy/ansible-role-logstash-forwarder)

An Ansible Role that installs Logstash Forwarder on RedHat/CentOS or Debian/Ubuntu.

**Note**: This role is well-tested on Debian/Ubuntu, but is still undergoing development for RedHat/CentOS. You've been warned!

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

The central Logstash server/port to which logstash-forwarder should connect:

    logstash_forwarder:
      servers:
        - host: localhost
          port: 5000

The location and filename of the SSL CA certificate logstash-forwarder will use to authenticate to the logstash server:

    logstash_forwarder:
      ssl:
        dir: /etc/pki/logstash
        ca_crt: logstash-forwarder-example.ca.crt

You can also provide the client key and certificate:

    logstash_forwarder:
      ssl:
        dir: /etc/pki/logstash
        ca_crt: logstash-forwarder-example.ca.crt
        client_key: logstash-forwarder-example.key
        client_crt: logstash-forwarder-example.crt


Configuration of files monitored by logstash-forwarder. You can add more sets of files by adding to the list with another set of files; see `defaults/main.yml` for an example.

    logstash_forwarder:
      files:
        - paths:
            - /var/log/messages
            - /var/log/auth.log
          fields:
            type: syslog

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
        - { role: geerlingguy.logstash-forwarder }

## Logstash-Forward configuration
You can install additional Logstash Forwarder configs in `/etc/logstash-forwarder.d/`

## License

MIT / BSD

## Author Information

This role was created in 2014 by [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/).
