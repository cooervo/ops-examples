```sh
cd ansible/01-install-python-playbook

docker build -t ansible-ssh-image .

docker run --rm -d -p 21:22 ansible-ssh-image

```

Troubleshoting:

```sh
ssh 0.0.0.0 -p 21 -l mateo
# password is secret123 as defined in Dockerfile 
```