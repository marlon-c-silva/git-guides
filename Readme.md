# Documentação Git: Principais Comandos

## Índice
- [O que é Git?](#o-que-é-git)
- [Configuração Inicial](#configuração-inicial)
- [Comandos Básicos](#comandos-básicos)
  - [git init](#git-init)
  - [git clone](#git-clone)
  - [git status](#git-status)
  - [git add](#git-add)
  - [git commit](#git-commit)
  - [git push](#git-push)
  - [git pull](#git-pull)
  - [git branch](#git-branch)
  - [git checkout](#git-checkout)
  - [git merge](#git-merge)
  - [git log](#git-log)
- [Outros Comandos Úteis](#outros-comandos-úteis)
  - [git stash](#git-stash)
  - [git remote](#git-remote)
  - [git rebase](#git-rebase)
---

## O que é Git?
O Git é um sistema de controle de versão distribuído usado para gerenciar e acompanhar mudanças no código-fonte ao longo do tempo. Ele facilita o trabalho em equipe, permitindo que múltiplas pessoas colaborem em projetos de maneira organizada e segura.

## Configuração Inicial

Antes de começar a usar o Git, você precisa configurá-lo com suas informações de usuário.

```bash
git config --global user.name "Seu Nome"
git config --global user.email "seuemail@exemplo.com"
```

## Comandos Básicos

### git init
Inicia um novo repositório Git no diretório atual.

```bash
git init
```

### git clone
Clona um repositório Git remoto para o seu computador.

```bash
git clone https://github.com/usuario/repo.git
```

Para clonar um repositório Git sem os commits anteriores (apenas trazendo os arquivos mais recentes, sem o histórico), você pode usar a opção `--depth` com o comando `git clone`. Isso cria um clone "raso" (shallow clone), que traz apenas o estado atual do repositório sem o histórico completo.

```bash
git clone --depth 1 https://github.com/usuario/repo.git
```

- `--depth 1`: Este parâmetro indica que você quer apenas o último commit do histórico (um clone raso).
- `1`: é o número de commits que você deseja clonar em seu repositorio considerando do commit mais recente ao mais antigo. 

- `https://github.com/usuario/repo.git`: O link do repositório que você deseja clonar.

Com isso, o Git irá baixar apenas os arquivos no estado atual, sem o histórico completo de commits, reduzindo o tamanho do clone e o tempo de download.

Caso deseja clonar o repositorio e trazer apenas pos ultimos 5 commits, basta utilizar:

```bash
git clone --depth 5 https://github.com/usuario/repo.git
```


### git status
Mostra o status dos arquivos no diretório de trabalho, informando quais foram modificados, adicionados ou estão aguardando commit.

```bash
git status
```

### git add
Adiciona arquivos modificados ou novos à área de preparação (staging), para que possam ser incluídos no próximo commit.

```bash
git add nome-do-arquivo
```

Ou para adicionar todos os arquivos modificados:

```bash
git add .
```

### git commit
Registra as mudanças no repositório local com uma mensagem descritiva.

```bash
git commit -m "Descrição das alterações"
```

### git push
Envia seus commits locais para o repositório remoto.

```bash
git push origin nome-da-branch
```

### git pull
Atualiza seu repositório local com as mudanças mais recentes do repositório remoto.

```bash
git pull
```

### git branch
Lista todas as branches existentes no repositório. Para criar uma nova branch, use `-b` seguido do nome da branch.

```bash
git branch
git branch -b nova-branch
```

### git checkout
Muda para outra branch ou revisões específicas.

```bash
git checkout nome-da-branch
```

### git merge
Combina mudanças de uma branch com outra. Esse comando deve ser executado a partir da branch que você desejar "mergear" com outra.

```bash
git merge nome-da-branch
```

### git log
Exibe o histórico de commits do repositório.

```bash
git log
```

## Outros Comandos Úteis

### git stash
Salva temporariamente as mudanças que não foram commitadas, permitindo que você limpe seu diretório de trabalho sem perder progresso.

```bash
git stash
```

Aqui está como você pode listar as stash e aplicar uma stash específica no Git:

#### **Listar todas as stash que você possui**
Para listar todas as stash armazenadas no repositório local, use o comando:

```bash
git stash list
```

Isso exibirá uma lista de todas as stash, com cada uma identificada por um índice (`stash@{n}`), onde `n` é o número da stash. Exemplo de saída:

```bash
stash@{0}: WIP on main: Commit message
stash@{1}: WIP on feature-branch: Commit message
stash@{2}: WIP on fix-branch: Commit message
```

#### **Aplicar uma stash específica**
Se quiser aplicar uma stash específica, você pode fazer isso utilizando o número dela na lista. Por exemplo, para aplicar a stash `stash@{1}`, use:

```bash
git stash apply stash@{1}
```

Se você quiser aplicar a stash mais recente (a primeira da lista), basta rodar o comando:

```bash
git stash apply
```

#### **Aplicar e remover a stash**
Se você quiser aplicar a stash e removê-la da lista ao mesmo tempo (ou seja, consumi-la), use o comando `git stash pop`:

```bash
git stash pop stash@{1}
```

Ou apenas:

```bash
git stash pop
```

Isso aplicará a stash mais recente e a removerá da lista de stash.

#### **Remover uma stash específica**
Se você quiser remover uma stash específica sem aplicá-la, use o comando `git stash drop`:

```bash
git stash drop stash@{1}
```

#### **Remover todas as stash**
Se você quiser limpar todas as stash de uma vez, use o comando:

```bash
git stash clear
```

### git remote
Mostra ou manipula repositórios remotos.

Para ver os repositórios remotos:

```bash
git remote -v
```

Para adicionar um novo repositório remoto:

```bash
git remote add origin https://github.com/usuario/repo.git
```

O comando `git remote` é usado para gerenciar os repositórios remotos de um projeto Git. Ele permite que você visualize, adicione, remova e gerencie conexões com repositórios hospedados em servidores remotos (como GitHub, GitLab, Bitbucket, etc.).

Aqui estão as principais coisas que você pode fazer com o comando `git remote`:

---

### **Listar repositórios remotos**

#### Comando:
```bash
git remote
```
Este comando lista todos os repositórios remotos associados ao seu repositório local. Ele exibe apenas os nomes dos repositórios.

#### Exemplo de saída:
```bash
origin
```

Para ver os URLs dos repositórios remotos, use a flag `-v` (verbose):

#### Comando:
```bash
git remote -v
```

#### Exemplo de saída:
```bash
origin  https://github.com/usuario/repo.git (fetch)
origin  https://github.com/usuario/repo.git (push)
```
Neste caso, o repositório remoto chamado `origin` está configurado tanto para "fetch" (baixar mudanças) quanto para "push" (enviar mudanças).

---

### **Adicionar um repositório remoto**

Se você quiser adicionar um novo repositório remoto, use o comando `git remote add`. 

#### Comando:
```bash
git remote add <nome-remoto> <url-remoto>
```

#### Exemplo:
```bash
git remote add origin https://github.com/usuario/novo-repo.git
```
Neste exemplo, estamos adicionando um repositório remoto chamado `origin` com a URL do GitHub.

Agora, você pode usar comandos como `git push origin main` para enviar seu trabalho para o repositório remoto que acabou de adicionar.

---

### **Renomear um repositório remoto**

Se você quiser renomear um repositório remoto, pode usar o comando `git remote rename`.

#### Comando:
```bash
git remote rename <nome-atual> <novo-nome>
```

#### Exemplo:
```bash
git remote rename origin upstream
```

Aqui, o repositório remoto chamado `origin` será renomeado para `upstream`.

---

### **Remover um repositório remoto**

Se você não quiser mais rastrear um repositório remoto, pode removê-lo com `git remote remove`.

#### Comando:
```bash
git remote remove <nome-remoto>
```

#### Exemplo:
```bash
git remote remove origin
```

Este comando remove a referência ao repositório remoto chamado `origin` do seu repositório local.

---

### **Alterar a URL de um repositório remoto**

Se a URL do repositório remoto mudou (por exemplo, você alterou o nome do repositório no GitHub ou mudou o protocolo de HTTP para SSH), você pode modificar a URL do repositório remoto usando `git remote set-url`.

#### Comando:
```bash
git remote set-url <nome-remoto> <nova-url>
```

#### Exemplo:
```bash
git remote set-url origin git@github.com:usuario/repo.git
```

Isso altera a URL do repositório `origin` para a nova URL SSH.

---

### **Exibir informações detalhadas sobre o repositório remoto**

Para ver informações detalhadas sobre um repositório remoto, incluindo as URLs de `fetch` e `push`, bem como o rastreamento de branches, você pode usar o comando `git remote show`.

#### Comando:
```bash
git remote show <nome-remoto>
```

#### Exemplo:
```bash
git remote show origin
```

#### Exemplo de saída:
```bash
* remote origin
  Fetch URL: https://github.com/usuario/repo.git
  Push URL: https://github.com/usuario/repo.git
  HEAD branch: main
  Remote branches:
    main                     tracked
  Local branch configured for 'git pull':
    main merges with remote main
  Local ref configured for 'git push':
    main pushes to main (up to date)
```

Isso mostra as informações sobre o repositório remoto `origin`, incluindo qual branch local está sincronizado com qual branch remota.

---

### **Verificar branches remotos**

O comando `git remote show` também permite verificar quais branches remotos estão disponíveis para sincronizar.

#### Comando:
```bash
git remote show <nome-remoto>
```

Isso exibe todas as branches disponíveis no repositório remoto, além de outras informações úteis.

---

#### Resumo dos principais comandos `git remote`:

- **Listar repositórios remotos:**
  ```bash
  git remote
  git remote -v
  ```

- **Adicionar um repositório remoto:**
  ```bash
  git remote add <nome-remoto> <url-remoto>
  ```

- **Renomear um repositório remoto:**
  ```bash
  git remote rename <nome-atual> <novo-nome>
  ```

- **Remover um repositório remoto:**
  ```bash
  git remote remove <nome-remoto>
  ```

- **Alterar a URL de um repositório remoto:**
  ```bash
  git remote set-url <nome-remoto> <nova-url>
  ```

- **Exibir detalhes de um repositório remoto:**
  ```bash
  git remote show <nome-remoto>
  ```

---


### git rebase
Reaplica seus commits em uma nova base, ajudando a manter o histórico linear.

```bash
git rebase nome-da-branch
```