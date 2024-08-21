```sh
cd ansible/01-install-python-playbook

docker build -t ansible-ssh-image .

docker run --rm -d -p 21:22 ansible-ssh-image

# attach docker interactive session 
ansible-playbook -i inventory.ini playbook.yml

```

Troubleshoting:

```sh
ssh 0.0.0.0 -p 22 -l mateo
# password is secret123 as defined in Dockerfile 
```