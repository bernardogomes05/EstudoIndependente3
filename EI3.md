# Curso Git 

# Arquivos do EI3 para disciplina de Manutencao e configuracao de software.

# CONFIG INICIAL DO GIT 

git config --global user.name "{seu nome}";
git config --global user.email "{seu email}";
git config --global core.editor {comando do editor}; EX: code, emacs, por padrao vim;
git config --list, lista todas as configs do seu GIT.

# INICIALIZAR UM REPOSITORIO

1. Criar a pasta do projeto: mkdir {nome do curso};
2. Entrar na pasta: cd {nome da pasta};
3. Iniciar o repositorio: git init.

        OBS: para criar um arquivo de texto e necessario colocar o codigo do editor e algum nome pro arquivo. EX: code EI3.md, abrira o arquivo no editor VSCode

# CICLO DE VIDA DOS STATUS DOS ARQUIVOS

1. UNTRACKED
-> Nao adionado/ nao reconhecido pelo GIT
-> Pode ser tambem quando o arquivo foi removido

2. UNMODIFIED 
-> Aquivo esperando a edicao

3. MODIFIED  
->Arquivo editado

4. STAGED
-> Arquivo esperando a confirmacao (commit) da edicao
-> Versao criada. 

5. UNMODIFIED 
-> Depois da confirmacao (commit) da edicao o arquivo volta a ser UNMODIFIED, ou seja, o arquivo ficara esperando nova edicao.

COMANDOS 

git status: mostra os status dos arquivos. Em qual pasta o user esta localizado, em qual etapa esta (MODIFIED, UNMODIFIED ou STAGED) e se tem algo para commitar.

git add: adiciona uma alteracao ao arquivo.

git commit: confirma as edicoes 
    commit -m: passa uma mensagem junto ao commit 
           -am: adiciona todos os arquivos editados + mensagem.
    BOAS PRATICAS: Sempre adicionar uma mensagem relacionado a mudanca feita no arquivo. EX: adicionou nova funcionalidade ou removeu alguma funcionalidade.


# VISUALIZANDO LOGS

git log: mostra a hash (id do commit), autor, data e uma mensagem relacionada ao commit
    log --decorate: mostra as branches do arquivo e para qual foi, se houve algum merge, quais as tags geradas.
    log --author="{nome do autor}": filtra as logs pelo nome do autor
    shortlog: mostra em ordem alfebetica quais foram os autores, quantos commits fizeram e quais foram
    shortlog -sn: mostra so os autores e quantos commits fizeram.
    log --graph: mostra em forma grafica os logs.
    show {hash do commit}: mostra quem fez, quando fez e o que fez detalhadamente relacionado ao commit passado pela HASH.

git diff: mostra qual foi a modificao no arquivo, adicao ou remocao 
        --name-only: mostra somente o nome do arquivo que foi modificado.

    DICA: Sempre bom usar o GIT DIFF antes de fazer um commmit    

# COMANDOS RESET

git checkout {nome do arquivo}: retorna o arquivo pra antes da edicao;
git reset HEAD {nome do arquivo}: retorna o arquivo que esta na fila staged para fila modified;
        --soft {hash do commit}: apenas volta o arquivo com a modificacao pronta, esperando o commit;
        --mixed {hash do commit}: volta o commit com os arquivos no MODIFIED;
        --hard {hash do commit}:  volta o commit inteiro, ou seja, ignora a existencia do commit e todas suas modicacoes. 
 
    obs: reset --soft --mixed --hard, usa-se depois que os commits foram confirmados
    obs 2: Sempre escolher o hash do commit anterior ao que voce deseja resetar. 
