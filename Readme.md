Infraestructure as Code - Learning how to configure terraform to build infra

main.tf -> arquivo de configuração da instância da máquina virtual (AWS)

terraforma init -> traz os arquivos necessários para a inicialização da instância

terraforma plan -> define as configurações a serem lançadas na ativação da máquina

terraform apply -> inicializa a instância com as configurações informadas

## Para acessar a máquina através de ssh:

```
ssh -i "acesso_teste.pem" ubuntu@ec2-52-67-87-53.sa-east-1.compute.amazonaws.com
```

Ao configurar um arquivo index.html dentro do servidor com um título (h1) com Ola mundo
Utilizamos o busybox para configurar um servidor http, com o comando:

```
nohup busybox httpd -f -p 8080 &
```

O nohup impede que o servidor seja encerrado

A partir daí, já conseguimos acessar a página através do IPV4 público, na porta 8080 (no caso da instância atual: http://52.67.87.53:8080/)

Para adicionar o Ansible, que irá gerenciar as configurações e ajustes do servidor, temos que criar dois arquivos: playbook.yml que irá conter os scripts que irão rodar no servidor, e hosts.yml que irá conter os hosts

Para executar o playbook com o ansible, utilizamos o comando:
```
ansible-playbook playbook.yml -u ubuntu --private-key acesso_teste.pem -i hosts.yml
```