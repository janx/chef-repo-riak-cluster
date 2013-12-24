Getting Started
---------------

1. Copy validation credentials into .chef of this directory.

2. Create a role for riak node:

  ```
  knife role create vagrant-riak
  ```

  Use the json below for the new created role:

  ```json
  {
    "name": "vagrant-riak",
    "default_attributes": {
    },
    "json_class": "Chef::Role",
    "run_list": [
      "recipe[riak]"
    ],
    "description": "Role for vagrant riak server",
    "chef_type": "role",
    "override_attributes": {
      "riak": {
        "install_method": "package",
        "package": {
          "version": {
            "major": 1,
            "minor": 2,
            "incremental": 1
          }
        },
        "core": {
          "cluster_name": "vagrant",
          "http": [["0.0.0.0", 8098]]
        },
        "kv": {
          "pb_ip": "0.0.0.0"
        }
      }
    }
  }
  ```

3. Modify ip and chef configurations in Vagrantfile to use your ip, organization and validation client.

4. `vagrant up`
