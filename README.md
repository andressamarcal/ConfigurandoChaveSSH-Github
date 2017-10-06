# Introdução de como criar sua chave SSH do Github #

## O que é chave SSH e para que ela serve? 
> É um meio serguro de autenticação, Key Pair, ou SSH Keys ou ainda Chave Pública, consiste em duas chaves uma pública que deve ser instalada no servidor remoto, e a outra chave privada que fica salva no seu computador, as duas juntas permitem que você conecte de forma segura a um servidor remoto usando o protocolo SSH ou SFTP. 

## Verificando se já possui SSH Key 
> Em ambiente Linux, é só digitar no terminal:
>` ls -al ~/.ssh `

> Lembre-se que seu servidor Git tem que ter suporte a transferência SSH. Se ele for GitHub, BitBucket ou GitLab não precisa se preocupar.

## Não tenho chave SSH, como configuro?
> Use o comando:
> `ssh-keygen -t rsa -b 4096 -C "seuemail@example.com"`
> A única coisa que você pode alterar ali é o argumento -C, ele cria comentários na chave. (Confie em mim, você vai precisar saber isso.)

> Nesse ponto, você vai receber uma mensagem de qual pasta você quer salvar sua key, NÃO ALTERE-A!
> Agora você terá que especificar uma senha (passphrase), mas ela não é obrigatória.

>Explicando o comando acima:
* Parâmetro -t específica o tipo de chave nesse caso usamos o algoritmo rsa para protocolo versão 2 outros possíveis valores são rsa1, dsa e ecdsa.
* Parâmetro -C adiciona um comentário à chave pública, é apenas uma maneira fácil de identificar a finalidade desta chave, o valor pode ser user@host.
* Parâmetro -b informa key size ou total de bits. O padrão é 2048, geralmente esse valor já é o suficiente para sua chave se quiser mais segurança use o valor máximo 4096.

>Pronto, agora você tem sua SSH Key no seu computador.

## Configurando sua chave pública para o Servidor
> Após executar o comando para gerar SSH keys dois arquivos serão salvos no diretório *~/ssh* por padrão os arquivos são `id_rsa` e `id_rsa.pub`, mas é possível criá-los com nomes e diretórios diferentes se for necessário.

> A chave pública, cujo a extensão é .pub, deve ser copiado para o servidor e o seu conteúdo é algo como:
*ssh-rsa AAAAB3NzaC1yc2EAAAADAQA .....*

> A chave privada tem o seguinte conteúdo:
*-----BEGIN RSA PRIVATE KEY-----MIIJKQIBAAKCAgEAzpHUcAE5w5e49Qw2S4cp17OmsIc1D8yfNR7y/ZLsf0382zsw.....*

### Passo a Passo para adicionar chave no Servidor:
* Vá nas configurações(settings) do seu usuário, no GitHub, BitBucket ou GitLab e procure por *SSH and GPG keys* ou similar. Você precisa adicionar uma nova Key(New SH Key);
* Copie todo o conteúdo do arquivo id_rsa.pub (naquela pasta "~/.ssh/", que foi criada) e cole na area Key, da pagina que você abriu;
* Existe um campo Title que você usa para identificar qual key é qual (geralmente eu coloco um identificador para cada PC, ex: PC Casa, PC Work.)
* Clique em submit ou Add SH Key.

> Sua chave foi inserida com sucesso. :)

> Agora você pode dar *git clone* com o link do SSH.
