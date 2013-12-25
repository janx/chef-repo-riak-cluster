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
      "description": "Role for vagrant riak server",
      "json_class": "Chef::Role",
      "default_attributes": {
      },
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
          "config": {
            "riak_core": {
              "http": [
                [
                  "__tuple",
                  "__string_0.0.0.0",
                  8098
                ]
              ]
            },
            "riak_api": {
              "pb_ip": "__string_0.0.0.0",
              "pb_port": 8087
            }
          }
        }
      },
      "chef_type": "role",
      "run_list": [
        "recipe[riak]"
      ],
      "env_run_lists": {
      }
    }

  ```

3. Modify ip and chef configurations in Vagrantfile to use your ip, organization and validation client.

4. `vagrant up`
