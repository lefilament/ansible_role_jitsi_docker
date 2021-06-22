docker_jitsi
============

This role deploys Jitsi components in Docker stack based on [Jitsi docker-compose](https://github.com/jitsi/docker-jitsi-meet/blob/master/examples/traefik-v2/docker-compose.yml).
The main repo for this role is on [Le Filament GitLab](https://sources.le-filament.com/lefilament/ansible-roles/docker_drawio.git)

Requirements
------------

None

Role Variables
--------------

Variables from default directory :
* jitsi_url: Jitsi URL for accessing the service
* jitsi_pad_url: Etherpad URL (external URL)
* jitsi_pad_internal_url: Etherpad internal URL (with protocol in front and port as needed, by default http://etherpad:9001)
* Jitsi inter-components communication passwords :
  * jibri_jicofo_comp_secret
  * jibri_jicofo_auth_pass
  * jitsi_jvb_auth_pass


Dependencies
------------

This role requires the following Ansible collection :
* community.docker

This Docker role supposes that Traefik is deployed as an inverseproxy in front of the deployed Dockers.
The following role is used by Le Filament for deploying Traefik : docker_server (https://sources.le-filament.com/lefilament/ansible-roles/docker_server)

This role may use an Etherpad deployed instance (https://sources.le-filament.com/lefilament/ansible-roles/docker_etherpad)

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: docker_jitsi }
      vars:
         - { jitsi_url: "jitsi.example.org" }
         - { jitsi_pad_url: "pad.le-filament.com" }
         - { jitsi_pad_internal_url: "http://etherpad:9001" }
         - { jibri_jicofo_comp_secret: "veryUnsecurePassToBeModified" }
         - { jibri_jicofo_auth_pass: "veryUnsecurePassToBeModified" }
         - { jitsi_jvb_auth_pass: "veryUnsecurePassToBeModified" }

License
-------

AGPL-3

Author Information
------------------

Le Filament (https://le-filament.com)
