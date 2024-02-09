# Linux Users/Groups Operation

## Task: add user and add to sudo group

Add new user and add to sudo (use adduser instead of useradd to set 1st password)

```bash
function create_user_with_id() {
    NUID=${1:-"5001"};
    USERNAME=${2:-"user"};
    PASSWORD=${3:-"password"};
    echo "Creating user with uid=${NUID} with username=${USERNAME} and password=${PASSWORD}"

    useradd -u ${NUID} ${USERNAME} -s /bin/bash -m -d /home/${USERNAME} \
    && echo ${USERNAME}:${PASSWORD} | chpasswd \
    && usermod -aG root ${USERNAME}
}

create_user_with_id 2001 user2001 pass2001
```

## Task: delete user

```bash
userdel user2001
```
