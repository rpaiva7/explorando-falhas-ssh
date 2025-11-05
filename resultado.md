## Explorando falhas no SSH

### 1º - Abrir o Metasploitable e o Kali Linux na Virtual Machine (VM). 

### 2º - No terminal do Kali Linux, criei duas pastas (~/home/kali) com o comando mkdir nomedapasta e avancei até a pasta kali com o comando cd nomedapasta para organizar melhor o trabalho.

### 3º - Acessar o Metasploit no Terminal Kali Linux

Comando: msfconsole

![msfconsole](https://i.imgur.com/H88lqOf.jpeg)

&nbsp;

### 4º - Encontrar os auxiliares de scanner que vão fazer a verificação de login. Vamos utilizar o primeiro encontrado, porém para utilizá-lo precisaremos de wordlists de usuário e senha.

Comando: search ssh_login

![search](https://i.imgur.com/DMDSO4m.jpeg)

&nbsp;

### 5º - Usar o auxiliary SSH de scanner encontrado. Quando as letras vermelhas entre parênteses aparecem significa que conseguimos utilizá-lo. 

Comando: use auxiliary/scanner/ssh/ssh_login 

![use](https://i.imgur.com/EZ6ZSMo.jpeg)

&nbsp;

### 6º - Pesquisar as infos para descobrirmos quais são os requisitos para obtermos acesso. Descobrimos que os requisitos são arquivos com usuários e senhas para um teste de força bruta

Comando: info 

![info](https://i.imgur.com/nErPiwX.jpeg)

&nbsp;

### 7º - A senha padrão do arquivo de senhas utilizado no teste é msfadmin, mas vamos criar o arquivo password e adicionar novas senhas para o teste de força bruta. Dentro do arquivo password criado, adicionamos as 3 palavras abaixo que serão as possíveis senhas, salvamos o arquivo com CTRL X e voltamos ao terminal: 

Comando: nano password.txt

test 

password

msfadmin

![password](https://i.imgur.com/gMl2KDw.jpeg)

&nbsp;

### 8º - Da mesma forma, criamos o arquivo user e dentro dele adicionamos as 3 palavras abaixo que serão utilizadas para o teste de força bruta, salvamos o arquivo com CTRL X e voltamos ao terminal:

Comando: nano user.txt

test

user

msfadmin

![user](https://i.imgur.com/r7AMhXY.jpeg)

&nbsp;

### 9º - Setar o host com o número IP da máquina-alvo

Comando: set rhosts nú.me.ro.ip

![set hosts](https://i.imgur.com/2zrCAnY.jpeg)

&nbsp;

### 10º - Agora precisamos definir os arquivos criados.

Comando: set USER_FILE ~/home/kali/usuarios.txt

Comando: set PASS_FILE ~/home/kali/senhas.txt 

Obs. Não esquecer de adicionar no path dos arquivos o sinal ~ caso seja necessário, senão o exploit não rodará.

![set files](https://i.imgur.com/6a2Iinx.jpeg)

&nbsp;

### 11º - Em seguida, rodamos o exploit

Comando: exploit

![exploit](https://i.imgur.com/VOe1Owe.jpeg)

&nbsp;

### 12º - O comando exploit criou a sessão com msfadmin como user e msfadmin como senha. Ele abriu uma sessão para nos conectarmos com o servidor remoto.

![success](https://i.imgur.com/NdQUJCB.jpeg)

&nbsp;

### 13º - Rodar o comando sessions para ver as sessões abertas com o nosso host-alvo

Comando: sessions 

![sessions](https://i.imgur.com/abN1X0X.jpeg)

&nbsp;

### 14º - Em seguida, escolho a sessão do meu host, nesse caso é a sessions 1, para iniciar a interação com o computador remoto.

Comando: sessions 1

![sessions 1](https://i.imgur.com/rymby5x.jpeg)

&nbsp;

### 15º - Em seguida aciono o comando ip addr no Terminal do Kali Linux para verificar se deu certo a invasão na máquina-alvo, nesse caso o metasploitable. 

Comando: ip addr

![ip addr](https://i.imgur.com/9i4FS1H.jpeg)

&nbsp;

### 16º - Aciono o comando ls para verificar quais pastas e arquivos estão no sistema invadido

Comando: ls

![ls](https://i.imgur.com/Q0FEjTt.jpeg)

&nbsp;

### 17º - Agora que estou dentro da máquina invadida, posso navegar por ela. Por exemplo, posso acionar o comando cd .. e em seguida o comando ls para verificar outros arquivos e pastas. Ou acionar o comando cd / e em seguida o ls para chegar no root e então navegar dentro do sistema operacional invadido.

![explore](https://i.imgur.com/wDpKf54.jpeg)

&nbsp;
