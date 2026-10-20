# 📖 Manual de Sobrevivência do Mantenedor
**Projeto:** `debian-nvidia-installer`  
**Mantenedor:** Wellington Freiman (`wellingtonfreiman2`)  
**E-mail:** `wellingtonfreiman89@proton.me`

---

## 📂 SITUAÇÃO 1: Estou no meu PC atual e quero continuar trabalhando
*(Use este passo se o seu computador está ligado normalmente e você só quer mexer no código).*

### Passo 1: Entrar na pasta do projeto
Você não precisa baixar nada da internet. A pasta já está no seu computador. Abra o terminal e digite:
cd ~/debian-nvidia-installer

### Passo 2: Criar uma "linha de trabalho" para a sua nova função
Para não bagunçar o código principal, crie uma ramificação segura. Mude o termo `minha-nova-funcao` para o que você estiver fazendo (ex: `ajuste-botoes`, `correcao-nvidia`):
git checkout -b feat/minha-nova-funcao

### Passo 3: Modificar os arquivos
Abra o editor de código e faça as alterações que desejar nos scripts. 
* Dica de Ouro: Se você estiver lançando uma versão nova do aplicativo, abra o arquivo chamado `VERSION` e mude o número lá dentro (ex: de `0.14.1` para `0.14.2`).

### Passo 4: Salvar e Enviar para o GitHub
Quando terminar as alterações e testar, digite estes 3 comandos em sequência para salvar seu trabalho na nuvem:
git add .
git commit -m "feat: adicionada nova funcionalidade ao instalador"
git push origin feat/minha-nova-funcao

---

## 💻 SITUAÇÃO 2: Formatei o PC (ou estou em um PC totalmente novo)
*(Use este passo se o seu computador foi limpo ou se você comprou um computador novo. Aqui você precisa configurar seus dados e baixar o projeto pela primeira vez).*

### Passo A: Configurar seus dados profissionais no terminal
Abra o terminal do computador novo, copie e cole este bloco inteiro de uma vez e aperte Enter:
sudo apt update && sudo apt install git -y
git config --global user.name "Wellington Freiman"
git config --global user.email "wellingtonfreiman89@proton.me"
git config --global github.user "wellingtonfreiman2"

### Passo B: Criar sua Chave de Conexão Segura (SSH)
Rode o comando abaixo. Quando o terminal começar a fazer perguntas na tela, não digite nada, apenas aperte a tecla `Enter` várias vezes até ele terminar e desenhar um quadrado com símbolos na tela:
ssh-keygen -t ed25519 -C "wellingtonfreiman89@proton.me"

### Passo C: Copiar e colar a chave dentro do site do GitHub
1. Digite este comando para exibir o código da sua chave na tela:
   cat ~/.ssh/id_ed25519.pub
2. Selecione e copie (Ctrl+Shift+C) todo o texto que apareceu na tela (ele começa com ssh-ed25519).
3. Abra o seu navegador de internet, faça login na sua conta e entre direto neste link: https://github.com
4. Clique no botão verde New SSH key.
5. No campo Title, digite um nome (ex: Meu Computador Debian).
6. No campo Key, cole o texto que você copiou do terminal e clique em Add SSH key.

### Passo D: Testar se o GitHub te reconheceu
Volte para o terminal e digite:
ssh -T git@github.com
*(Se o terminal exibir uma pergunta com yes/no, digite yes e aperte Enter).*  
A resposta correta na tela deve ser: Hi wellingtonfreiman2! You've successfully authenticated...

### Passo E: Baixar o projeto da internet pela primeira vez
Agora que o computador novo está autorizado, rode estes 3 comandos para baixar seus arquivos com segurança para a sua pasta principal:
cd ~
git clone git@github.com:wellingtonfreiman2/debian-nvidia-installer.git
cd debian-nvidia-installer

---

## 🛑 As 2 Regras de Ouro do Projeto:
1. Nunca envie arquivos .deb para o Git: Nós já configuramos o arquivo .gitignore para impedir que arquivos compilados pesados subam para a nuvem. O Git serve apenas para salvar seus códigos em texto.
2. Como saber se posso fechar o terminal? Na dúvida se esqueceu de salvar algo, digite git status. Se a resposta for nothing to commit, working tree clean, tudo foi salvo perfeitamente e você pode fechar o terminal e descansar!
