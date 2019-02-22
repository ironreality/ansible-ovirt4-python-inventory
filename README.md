# oVirt dynamic inventory with fact caching

After the cache settings are activated the fact cache is being written to **fact_cache/** subdirectory

The original Ansible's script is [here](https://raw.githubusercontent.com/ansible/ansible/devel/contrib/inventory/ovirt4.py)

## Ansible fact caching

To enable the json fact caching (suppose you're in the root of your Ansible project):

```
mkdir fact_cache

cat >> ovirt.ini<<EOF
ovirt_cache = True
ovirt_cache_path = fact_cache/ovirt_inventory.cache
ovirt_cache_max_age = 3600
EOF

export ANSIBLE_CACHE_PLUGIN=jsonfile
export ANSIBLE_CACHE_PLUGIN_TIMEOUT=36000
export ANSIBLE_CACHE_PLUGIN_CONNECTION=fact_cache/
```
