# SSH

## Adding a User

```bash
$ adduser newuser
```

## Granting a User Sudo Privileges


```bash
$ groups newuser
$ usermod -aG sudo newuser
$ visudo

root    ALL=(ALL:ALL) ALL
newuser ALL=(ALL:ALL) ALL
```

## Delete a User

```bash
$ deluser newuser
```

If, instead, you want to delete the user’s home directory when the user is deleted, you can issue the following command as root:

```bash
$ deluser --remove-home newuser
```

```bash
$ visudo

root    ALL=(ALL:ALL) ALL
newuser ALL=(ALL:ALL) ALL   # DELETE THIS LINE
```