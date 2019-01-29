Create this directories structure:
.
├── docker-compose.yml
├── Dockerfile
├── dump
│   └── myDb.sql
├── sessions
└── www
    └── index.php

    
    
#Scritp para definicao do servidores git
#!/bin/bash
 echo "Qual servidor ativar?: \n1-Bitbucket \n2-Github \n3-Gitlab"
 

read resp

if [ $resp = "1" ];
    then
		echo "#conexao bitbucket" 					>  ~/.ssh/config
		echo "Host bitbucket.org" 					>> ~/.ssh/config
		echo "Hostname  altssh.bitbucket.org"   	>> ~/.ssh/config
		echo "Port  443" 							>> ~/.ssh/config
		serv="bitbucket"
elif [ $resp = "2" ];
	then
		echo "#conexao Github"  					> ~/.ssh/config
		echo "Host github.com" 						>> ~/.ssh/config
		echo "Hostname ssh.github.com"				>> ~/.ssh/config
		echo "Port 443"								>> ~/.ssh/config
		serv="Github"
elif [ $resp = "3" ];
	then
		echo "#conexao repositorio semge" 			> ~/.ssh/config
		echo "Host gitlab.com"						>> ~/.ssh/config
		echo "Hostname altssh.gitlab.com"			>> ~/.ssh/config
		echo "User git"								>> ~/.ssh/config
		echo "Port 443"								>> ~/.ssh/config
		echo "PreferredAuthentications publickey"	>> ~/.ssh/config
		echo "#IdentityFile ~/.ssh/id_rsa"			>> ~/.ssh/config
		serv="gitlab"
fi

echo "Configuracao criada com servidor do $serv"
cat ~/.ssh/config
 
