Pré-requisitos
Seleção do Recipe
Adicione o caminho do singularity recipe desejado na variável RECIPE no github (projeto >> Settings >> Secrets >> New Secret).

Template Integração Contínua Github
Esse projeto o template para uso do cluster da UFSCar, contendo integração contínua com o Google Drive e Amazon S3.

Requisitos para Google Drive
Entre no console de credenciais de API do Google
Se ainda não houver um projeto, crie um com permissão para a "Google Drive API".
Clique em "Criar credenciais".
Selecione "ID do cliente do OAuth".
Em "Tipo de aplicativo", selecione "App para computador".
Dê um nome de identificação para as credenciais e clique em "criar". Vão aparecer dois dados ("Seu ID de cliente" e "Sua chave secreta de cliente"), precisaremos dos dois no passo seguinte.
Acesse o cluster, execute o comando rclone config e forneça as seguintes informações quando solicitado:
n/s/q> n
name> cloud
Storage> 13
client_id> conteúdo de "Seu ID de cliente"
client_secret> conteúdo de "Sua chave secreta de cliente"
scope> 1
root_folder_id> deixe em branco
service_account_file> deixe em branco
y/n> deixe em branco
y/n> n

Copie o url e cole no navegador no computador local. Autorize e:

Enter verification code> código fornecido pelo navegador após autorização
y/n> deixe em branco
y/e/d> deixe em branco
e/n/d/r/c/s/q> q
A configuração até agora servirá para transferência de dados do cluster para a nuvem e vice-e-versa. A partir de agora vamos configurar a integração contínua no github.

Execute o comando:
echo $(cat ~/.config/rclone/rclone.conf | base64 --wrap=0)
Copie a saída e adicione à variável RCLONE_CONF no github.
Adicione no github à variável COLLECTION_CONTAINER /path/to/project, esse será o caminho cujo container vai ser disponibilizado no seu Google Drive no formato recipe_name_DateTime.simg.
Requisitos para Amazon S3
Entre na AWS
Clique na seta ao lado de seu nome de usuário e em "My Security Credentials".
Na seção "Access Keys", clique em "Create New Access Key".
Na janela que aparece, clique em "Show Access Key".
Acesse o cluster, execute o comando rclone config e forneça as seguintes informações quando solicitado:
n/s/q> n
name> cloud
Storage> 4
provider> 1
env_auth> 1
access_key_id> conteúdo de "Access Key ID"
secret_access_key> conteúdo de "Secret Access Key"
region> 16
endpoint> deixe em branco
location_constraint> 16
acl> deixe em branco
server_side_encryption> deixe em branco
sse_kms_key_id> deixe em branco
storage_class> deixe em branco
y/n> deixe em branco
y/e/d> deixe em branco
e/n/d/r/c/s/q> q
A configuração até agora servirá para transferência de dados do cluster para a nuvem e vice-e-versa. A partir de agora vamos configurar a integração contínua no github.

Execute o comando:
echo $(cat ~/.config/rclone/rclone.conf | base64 --wrap=0)
Copie a saída e adicione à variável RCLONE_CONF no github.
Adicione no github à variável COLLECTION_CONTAINER /path/to/project, esse será o caminho cujo container vai ser disponibilizado no seu Google Drive no formato recipe_name_DateTime.simg
