# Simulacao-de-Brute-Force-Medusa-Kali-Linux
Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux


1- Introdução

Este projeto tem como objetivo estudar e demonstrar, em um ambiente controlado, como funcionam os ataques de força bruta contra diferentes serviços e aplicações.
Para realizar as simulações, são utilizadas ferramentas de segurança presentes no Kali Linux, com destaque para o Medusa, além de ambientes vulneráveis preparados para fins educacionais.
O projeto também busca compreender os riscos relacionados ao uso de senhas fracas e a importância de implementar medidas de proteção contra tentativas não autorizadas de acesso.

2- Ambiente utilizado

Sistema operacional: Kali Linux;
Virtualização: Oracle VirtualBox;
Máquina vulnerável: Metasploitable 2;
Aplicação WEB: DVWA;
Ferramenta de auditoria: Medusa, Nmap;
Tipo de rede: Host-Only;


<img width="1920" height="1025" alt="Captura de tela de 2026-11-02 19-35-37" src="https://github.com/user-attachments/assets/4a1d2188-1c76-46ad-9bb2-35d95456fbdb" />


------------------------------------------------------------------------------------------------------------
Primeiro cenário - Ataque de força bruta em FTP

Objetivo:
Entender como funciona um ataque brute-force contra o serviço em questão, utilizando uma ferramente de auditoria para testar uma combinação de usuários e senhas criadas durante o curso DIO.ME

Ferramenta Utilizada:
Foi utilizada durante o teste a ferramenta medusa com auxilio no nmap.

Procedimento:
Foi utilizado o Kali para realizar tentativas de autenticação contra o serviço FTP disponibilizado no ambiente vulnerável.
Após a auditoria de portas, verificação completa com nmap, foi utilizado duas listas, uma contendo senhas e outra usuários para testar diversas combinações, tendo assim o êxito na conclusão do teste.

comandos utilizados:
'nmap -sS -sV IP ' - Para fazer auditoria de todas as portas abertas no ip vulnerável juntamente com suas versões.
'medusa -h IP -U users.txt -P pass.txt -M ftp -t 6' - Para fazer o processo de brute-force utilizando as wordlists.

Resultados:
Como esperado, obtivemos conhecimento do usuário e da senha, necessária para ter acesso ao serviço FTP do alvo.

Analise:
O serviço pode apresentar risco se mal configurado, se utilizado com senhas fracas, podendo ser substituido por uma versão mais segura (SFTP) quando aplicável

Medidas de prevenção:
Senhas fortes e exclusivas.

-----------------------------------------------------------------------------------------------------------

Segundo cenário - Ataque de força bruta em formulário Web (DVWA)

Objetivo:
Entender como ataques automatizados em formulários web com pouca segurança podem ser um problema para a empresa, colocando em cheque possíveis informações sensíveis.

Ambiente utilizado:
DVWA (Damn Vulnerable Web Application), uma aplicação desenvolvida para estudos de cybersegurança.

Procedimento:
Foi utilizado um formulário de autenticação do DVWA para simular tentativas automatizadas de login.
Esse teste permitiu observar como as ferramentas podem automatizar o envio de credenciais e identificar possíveis falhas na aplicação em questão.

Comandos utilizados:
"medusa -h 192.168.56.102 -U users.txt -P pass.txt -M http \ -m PAGE:'/dvwa/login.php' \ -m FORM:'username=^USER^&password=^PASS^&Login=Login' \ -m 'FAIL=Login failed' -t 6 -v 4"

Resultado:
Após a execução do comando o Medusa iniciou o ataque, descobrindo as credenciais poucos segundos após o inicio.


Análise:
Formulários sem mecanismos adequedos podem permitir que atacantes realizem várias tentativas de autenticação sem dificuldades, pondo em risco a empresa e seus usuários.

Medidas de prevenção:
Limitar as tentativas de login, adotar a politica de senhar fortes, verificação de dois fatores, monitorar as tentativas repetidas de autenticação com sistemas.

-------------------------------------------------------------------------------------------------------------
Terceiro cenário - Password Spraying em SMB
