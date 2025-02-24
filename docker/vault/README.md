# HashiCorp Vault (Dev-Mode)

## Inisialisasi Vault

```bash
$ vault operator init

Example :

Unseal Key 1:
Unseal Key 2:
Unseal Key 3:
Unseal Key 4:
Unseal Key 5:

Initial Root Token:
```

## KV Secrets Engine

```bash
$ vault secrets enable -path=my-secret/ kv
$ vault secrets list

$ vault kv put my-secret/demo-api-token token-name=demo-api-token token-secret=SuperSecret
$ vault kv get my-secret/demo-api-token

$ vault kv --help
```

## Generate Secret

```bash
$ cd policy
$ vault write sys/policies/password/generate-secret policy=@generate-secret.hcl
$ vault read sys/policies/password/generate-secret/generate

$ export PASSWORD=$(vault read -field=password sys/policies/password/generate-secret/generate)
$ vault kv put my-secret/generated-secret password=${PASSWORD}

$ vault kv get my-secret/generated-secret
```

## Dynamic Secret

> Note : Dynamic Secret hanya akan dibuat ketika diakses saja.

```bash
$ vault secrets enable database
$ vault secrets list
```

### Connect Vault to Database

```bash
$ vault write database/config/demo-database \
plugin_name=mysql-database-plugin \
connection_url="{{username}}:{{password}}@tcp(127.0.0.1:3306)/" \
allowed_roles="*" \
username="root" \
password="root"
```

### Membuat Database Role (Admin)

```bash
$ vault write database/roles/db-admin \
db_name=demo-database \
creation_statements="CREATE USER '{{name}}'@'%' IDENTIFIED BY '{{password}}';" \
creation_statements="GRANT ALL PRIVILEGES ON *.* TO '{{name}}'@'%';" \
revocation_statements="DROP USER '{{name}}'@'%';" \
default_ttl="1h" \
max_ttl="24h"
```

### Membuat Database Role (Read Only)

```bash
$ vault write database/roles/db-read-only \
db_name=demo-database \
creation_statements="CREATE USER '{{name}}'@'%' IDENTIFIED BY '{{password}}';" \
creation_statements="GRANT SELECT ON *.* TO '{{name}}'@'%';" \
revocation_statements="DROP USER '{{name}}'@'%';" \
default_ttl="1h" \
max_ttl="24h"
```

### Generate Dynamic Secret (Admin)

```bash
$ vault read database/creds/db-admin
```

### Generate Dynamic Secret (Read Only)

```bash
$ vault read database/creds/db-read-only
```

### Mengelola Dynamic Secret

```bash
$ vault list sys/leases/lookup/database/creds/db-admin
$ vault lease revoke database/creds/db-admin/{{key}}
```