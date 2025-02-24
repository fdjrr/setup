# HashiCorp Vault (Dev-Mode)

## Cara Akses Vault

```bash
$ docker exec -it vault-dev sh
$ vault status
```

```bash
$ wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
$ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
$ sudo apt update && sudo apt install vault
```

```bash
$ export VAULT_ADDR="http://127.0.0.1:8200"
$ export VAULT_TOKEN=""
$ vault status
$ vault secrets list
```

```bash
$ curl -s http://127.0.0.1:8200/v1/sys/seal-status
```

## Cara Seal / Unseal

```bash
$ vault operator seal
$ vault operator unseal
```

> Note : Unseal Key cek di `docker logs vault-dev -f`