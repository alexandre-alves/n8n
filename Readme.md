Para apenas testar use rode sem ssl
Docker Run
$ docker run -it --rm --name n8n -p 5678:5678 -e N8N_SECURE_COOKIE=false -v n8n_data:/home/node/.n8n docker.n8n.io/n8nio/n8n

Use o docker-compose.yml e defina suas variavesi de ambiente:
.env
~~~~
# Nome do domínio principal a ser servido (ex: example.com)
DOMAIN_NAME=example.com

# Subdomínio a ser usado para acesso (ex: n8n)
SUBDOMAIN=n8n

# A combinação de DOMAIN_NAME e SUBDOMAIN define a URL de acesso ao n8n
# O exemplo acima resultaria em: https://n8n.example.com

# Fuso horário opcional para definir o padrão usado pelo nó Cron
# Se não definido, o horário de Nova York será usado
GENERIC_TIMEZONE=Europe/Berlin

# Endereço de email a ser usado para a criação do certificado SSL
SSL_EMAIL=user@example.com
~~~~

Se você estiver planejando ler/gravar arquivos locais com o n8n (por exemplo, usando o nó Read/Write Files from Disk), precisará configurar um diretório de dados para esses arquivos aqui. Se você estiver executando o n8n como usuário root, adicione isso em volumes para o serviço n8n:

/local-files:/files
Se você estiver executando o n8n como um usuário não root, adicione isso em volumes para o serviço n8n:

/home/<SEU NOME DE USUÁRIO>/n8n-local-files:/files
Agora você poderá gravar arquivos no diretório /files no n8n e eles aparecerão em seu servidor em /local-files ou /home/<SEU NOME DE USUÁRIO>/n8n-local-files, respectivamente.
