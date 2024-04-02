# ansible-role-hashicorp-vault-unseal

An Ansible role that unseals HashiCorp Vault.

## Requirements

No specific pre-requisites.

## Role Variables

### `hashicorp_vault_address`

The address of HashiCorp Vault. Defaults to `https://127.0.0.1:8200`.

### `hashicorp_vault_validate_certs`

Whether or not you would want to validate certs when using a TLS connection. Defaults to `true`.

### `hashicorp_vault_api_version`

The version of the HashiCorp Vault API to use. Defaults to `v1`.

### `hashicorp_vault_seal_status_endpoint`

The API endpoint to determine the sealed state. Defaults to `/sys/seal-status`.

### `hashicorp_vault_unseal_endpoint`

The API endpoint to unseal the Vault. Defaults to `/sys/unseal`.

### `hashicorp_vault_unseal_key_threshold`

The number of key shares that are required to unseal the Vault. Defaults to `3`.

### `hashicorp_vault_unseal_keys`

An Ansible Vault encrypted list of the unseal keys. Example code to encrypt this below.

```shell
ansible-vault encrypt_string '["key1", "key2", "key3", "key4", "key5"]' --name 'hashicorp_vault_unseal_keys'
```

## Dependencies

No dependencies.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yml
- name: Unseal HashiCorp Vault
  hosts: vault_servers

  roles:
    - role: chrisvanmeer.hashicorp_vault_unseal
      vars:
        hashicorp_vault_address: http://127.0.0.1:8200
        hashicorp_vault_validate_certs: false
        hashicorp_vault_unseal_key_threshold: 2
        hashicorp_vault_unseal_keys: !vault |
          $ANSIBLE_VAULT;1.1;AES256
          66353835326362306531386135353938316637666362353666373336323037623065653961303231
          6437343363623266313437323638636436333035323263330a366366643661666364623363656339
          34343761313431386235373136396136363834353833633936633766306464316230313432383864
          3835343766623336660a366635623166383936303534306631303732656361636533323431396131
          3436
```

## License

EUPL-1.2

## Author Information

- Chris van Meer <c.v.meer@atcomputing.nl>
