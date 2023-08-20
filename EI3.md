# Curso Git 

# Arquivos do EI3 para disciplina de Manutenção e configuração de software.

# CONFIG INICIAL DO GIT 

git config --global user.name "{seu nome}";
git config --global user.email "{seu email}";
git config --global core.editor {comando do editor}; EX: code, emacs, por padrao vim;
git config --list, lista todas as configs do seu GIT.

# INICIALIZAR UM REPOSITÓRIO

1. Criar a pasta do projeto: mkdir {nome do curso};
2. Entrar na pasta: cd {nome da pasta};
3. Iniciar o repositório: git init.

        OBS: Para criar um arquivo de texto e necessário colocar o código do editor e algum nome pro arquivo. EX: code EI3.md, abrira o arquivo no editor VSCode

# CICLO DE VIDA DOS STATUS DOS ARQUIVOS

1. UNTRACKED
-> Não adionado/ não reconhecido pelo GIT
-> Pode ser também quando o arquivo foi removido

2. UNMODIFIED 
-> Aquivo esperando a edição

3. MODIFIED  
->Arquivo editado

4. STAGED
-> Arquivo esperando a confirmação (commit) da edição
-> Versao criada. 

5. UNMODIFIED 
-> Depois da confirmação (commit) da edção o arquivo volta a ser UNMODIFIED, ou seja, o arquivo ficara esperando nova edição.

COMANDOS 

git status: mostra os status dos arquivos. Em qual pasta o user esta localizado, em qual etapa esta (MODIFIED, UNMODIFIED ou STAGED) e se tem algo para commitar.

git add: adiciona uma alteração ao arquivo.

git commit: confirma as edições 
    commit -m: passa uma mensagem junto ao commit 
           -am: adiciona todos os arquivos editados + mensagem.
    BOAS PRÁTICAS: Sempre adicionar uma mensagem relacionado a mudança feita no arquivo. EX: adicionou nova funcionalidade ou removeu alguma funcionalidade.


# VISUALIZANDO LOGS

git log: mostra a hash (id do commit), autor, data e uma mensagem relacionada ao commit
    log --decorate: mostra as branches do arquivo e para qual branch foi, se houve algum merge, quais as tags geradas.
    log --author="{nome do autor}": filtra as logs pelo nome do autor
    shortlog: mostra em ordem alfebética quais foram os autores, quantos commits fizeram e quais foram
    shortlog -sn: mostra só os autores e quantos commits fizeram.
    log --graph: mostra em forma gráfica os logs.
    show {hash do commit}: mostra quem fez, quando fez e o que fez detalhadamente relacionado ao commit passado pela HASH.

git diff: mostra qual foi a modifição no arquivo, adição ou remoção 
        --name-only: mostra somente o nome do arquivo que foi modificado.

    DICA: Sempre bom usar o GIT DIFF antes de fazer um commmit    

# COMANDOS RESET

git checkout {nome do arquivo}: retorna o arquivo pra antes da edição;
git reset HEAD {nome do arquivo}: retorna o arquivo que está na fila staged para fila modified;
        --soft {hash do commit}: apenas volta o arquivo com a modificação pronta, esperando o commit;
        --mixed {hash do commit}: volta o commit com os arquivos no MODIFIED;
        --hard {hash do commit}:  volta o commit inteiro, ou seja, ignora a existência do commit e todas suas modicações. 
 
    obs: reset --soft --mixed --hard, usa-se depois que os commits foram confirmados
    obs 2: Sempre escolher o hash do commit anterior ao que voce deseja resetar. 

# GitHub

# Chave SSH

    Para subir um arquivo no repositório remoto é necessario gerar e adicionar uma chave SSH 

1. Para gerar a chave SSH usa-se esse comando no terminal   
        ssh-keygen -t rsa -b 4096 -C "{seu email cadastrado no GitHub}"
2. Ao gerar a chave acesse o diretório contendo id_rsa.pub, ao acessar entre no GitHub
3. Va nas configurações de acesso e procure SSH and GPG keys.
4. Clique adicionar nova chave SSH, de um titulo e copie a chave no campo indicado. 

# Ligação repositório local e remoto

    obs: Para ligar um repositório local a um remoto é necessário alguns comandos.

Se o repositório local ainda não foi criado é necessário usar os comandos asseguir

    git init 
    git add {nome do arquivo e tipo de extenção}
    git commit -m "alguma mensagem para o primeiro commit"
    git remote add origin {URL do repositório}
    git push -u origin master

Se o repositório local já foi criado é só usar esse dois comandos

    git remote add origin {URL do repositório}
    git push -u origin master

# Atualizar repositório remoto

Para atualizar um repositório remoto é necessário confirmar um commit no repositório local e em seguida usar o comando 

    git push origin master

# Clonar repositórios remotos

Para clona/copiar um repositório remoto usa-se o comando 

    git clone {URL do repositório + um nome para a cópia}

# FORK 

O QUE É: fork permite pegar outros repositórios remotos que não são seus e fazer contribuições. 
EX: vi que album repositório tem um erro e eu desejo arrumar-lo, para criar um FORK é necesário acessar esse repositório e clicar na opção de FORK no canto superior direito.

FORK e CLONE são diferentes porque o clone só é possivel fazer copias para voçe, já o FORK é possivel editar os arquivos de outra pessoa e atualiza-los.

# BRANCH 

O QUE É: branch é como se fosse um ponteiro móvel que mostra em qual commit voçe está. Ao criar um repositório voçe vai estar no branch master, que é o branch inicial. 
Também é possivel criar novos branches e apontar para o mesmo repositório em que se encontra ou outros repositórios.

# Usos dos branches

VANTAGENS 

- Poder modificar sem alterar o local principal(master), ou seja, é possivel corrigir um bug enquanto tem outras pessoas trabalhando no branch principal.

- Facilmente "desligavel", ou seja, é possivel criar e apagar branches facilmente.

- Multiplas pessoas trabalhando, ou seja, várias pessoas podem estar trabalhando em diversos outros branches sem atrapalhar uns aos outros.

- Evita conflitos. 

# Criar um branch 

    git checkout -b {nome do branch}

git branch: mostra quais os branches existentes e em qual voçe está localizado
    checkout -b: específica que está sendo criado um branch
    checkout {nome do branch}: voçe vai ir para o branch especificado.
    branch -D {nome do branch}: deleta um branch

# Unir branches - MERGE ou REBASE

MERGE 

Mais complexo

Cria um commit extra para juntar com o branch master 

PROS 

- Operação não destrutiva, ele apenas cria um novo commit para depois juntar todos. 


CONTRAS

- Commit extra, commit que não adiciona nada novo, apenas junta outros commits.

- Histórico poluído.

REBASE 

Entendimento mais simples

Coloca todas as mudanças feitas para frente da linha (fast forward).

PROS

- Evita commits extras 

- Histórico se mantém linear 

CONTRAS 

- Perde ordem cronológica, ou seja, se há duas pessoas trabalhando no mesmo branch, se eu mudar o histórico (confirmar um commit) não será possivel da outra pessoa aplicar as mudanças dela.




