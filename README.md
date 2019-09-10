Role Name
=========

Uploads OpenShift Images from the local machine to an on-premise Container Registry.
Another role is used to Download OpenShift Images for a disconnected/offline
Container Registry for use with a Red Hat OpenShift install.

Requirements
------------

Requires Skopeo for uploading Container Images.

Role Variables
--------------

The following variables may need to be set, defaults found in `defaults/main/*.yml`:

The Destination Registry credentials and URL variables are as follow:
    dest_registry_user: ""
    dest_registry_passwd: ""
    dest_registry_url: "registry.example.com/"

You should also have three image lists that define the images to download for OpenShift (as YAML)
    docker_image_list_required
    docker_image_list_optional
    docker_image_list_s2i

The specific container image versions could be set as follow:
    ocp_container_tag_major: "v3.11"
    ocp_container_tag_full: "v3.11.135"
    ocp_container_tag_pod: "v3.11.98"
    ocp_container_tag_deployer: "v3.11.135"
    ocp_container_tag_etcd: "3.2.22"
    s2i_container_tag: "latest"

Dependencies
------------

None

Example Playbook
----------------

- hosts: servers
  roles:
    - role: snelson_redhat.ocp_images.transfer
      dest_registry_url: "registry.example.com/"
      dest_registry_user: redhataccessuser
      dest_registry_passwd: redhataccesspasswd

License
-------

MIT / BSD

Author Information
------------------

This role was written in 2019 by Sean Nelson
