# Fluxo de versionamento com git flow

O git-flow é um conjunto de extensões para o git que provê operações de alto-nível para repositórios usando o modelo de branches do Vincent Driessen.

![git-flow](git-model@2x.png)




## 1. Instalação
O git flow funciona no macOS, Linux e no Windows

### 1.1. Linux
``` sh
$ apt-get install git-flow
```

### 1.2. Windows (Cygwin)
``` sh
$ wget -q -O - --no-check-certificate https://raw.github.com/petervanderdoes/gitflow-avh/develop/contrib/gitflow-installer.sh install stable | bash
```

### 1.3. Windows 

[Instalação e configuração do Sourcetree no windows](https://git.digicade.com.br/templates/gitflow/src/master/windows/README.md)


## 2. Inicialização
O git-flow precisa ser inicializado para personalizar a configuração de seu projeto.

Comece o uso do git-flow fazendo sua inicialização dentro de um repositório git existente:


``` sh
$ git flow init -d
```


## 3. Fluxo

### 3.1. Funcionalidades

#### 3.1.1. Começar uma nova funcionalidade
O desenvolvimento de novas funcionalidades começa no branch 'develop'.

![Nova Funcionalidade](start-feature.png)

##### 3.1.1.1. Linux

Comece o desenvolvimento de uma nova funcionalidade com

``` sh
$ git flow feature start MYFEATURE
```

Esse comando cria um novo branch da funcionalidade baseado no 'develop' e alterna para ele

##### 3.1.1.2. Windows Sourcetree

Para começar o desenvolvimento de uma nova funcionalidade no Sourcetree;
Acione o botão Git Flow:

![Nova funcionalidade](novaFeatureSourcetree.png)

Podemos criar novas funcionalidades a partir do develop (padrão) ou em casos que seja necessário criar a partir de um commit também é possível, sendo necessário somente selecionar a partir de qual commit a funcionalidade deve ser criada. Atribuir um nome conforme padrão do projeto.

![Nova funcionalidade 2](novaFeature2Sourcetree.png)


#### 3.1.2. Publicar uma funcionalidade
Você está desenvolvendo uma funcionalidade colaborativamente? 
Publique uma funcionalidade para o servidor remoto, assim ela pode ser utilizada por outros usuários.

##### 3.1.2.1. Linux

``` sh
$ git flow feature publish MYFEATURE
```

##### 3.1.2.2. Windows Sourcetree

![Publicar funcionalidade](publicarFeatureSourcetree.png)

![Publicar funcionalidade](publicarFeature2Sourcetree.png)


#### 3.1.3. Obter uma funcionalidade publicada
Obtenha uma funcionalidade publicada por outro usuário e acompanhe as alterações remotas.

##### 3.1.3.1. Linux
``` sh
$ git flow feature track MYFEATURE
```
##### 3.1.3.2. Windows Sourcetree

![Obter funcionalidade](obterFeatureSourcetree.png)

#### 3.1.4. Finalizar uma funcionalidade
Finaliza o desenvolvimento de uma funcionalidade. Esse comando faz o seguinte

![Nova Funcionalidade](end-feature.png)

Mescla MYFEATURE no 'develop'
Remove o branch da funcionalidade
Volta para o branch 'develop'

##### 3.1.4.1. Linux

``` sh
$ git flow feature finish MYFEATURE
```

##### 3.1.4.2. Windows Sourcetree

Para finalizar uma funcionalidade basta acionar o comando do Git Flow, ir em "Outra Ação" e "Finalizar Recurso":

![Finalizar funcionalidade](finalizarFeatureSourcetree.png)


### 3.2. Versões
Auxilia a preparação de uma nova versão de produção
Permite correções de bugs menores e a preparação de metadados de uma versão

#### 3.2.1. Começar uma nova versão
Para começar uma versão, use o comando git flow release. Ele
cria um branch da versão baseado no branch 'develop'.

![Começar ma versão](start-release.png)

##### 3.2.1.1. Linux

``` sh
$ git flow release start RELEASE [BASE]
```

Você pode opcionalmente fornecer um hash sha-1 do commit [BASE] de onde começar a versão. O commit precisa estar no branch 'develop'

##### 3.2.1.2. Windows Sourcetree

Para começar o desenvolvimento de uma nova versão no Sourcetree;
Acione o botão Git Flow:

![Nova versão](novaReleaseSourcetree.png)

Podemos criar novas versões a partir do develop (padrão) ou em casos que seja necessário criar a partir de um commit também é possível, sendo necessário somente selecionar a partir de qual commit a versão deve ser criada. Atribuir um nome conforme padrão do projeto.

![Nova versão 2](novaRelease2Sourcetree.png)



#### 3.2.2. Publicar uma versão
É sensato publicar o branch da versão depois de criá-lo, para permitir commits por outros desenvolvedores. É semelhante à publicação de uma funcionalidade com o comando:

##### 3.2.2.1. Linux

``` sh
$ git flow release publish RELEASE
```

##### 3.2.2.2. Windows Sourcetree

![Publicar funcionalidade](publicarFeatureSourcetree.png)

![Publicar funcionalidade](publicarFeature2Sourcetree.png)


#### 3.2.3. Obter uma versão publicada
Você pode acompanhar uma versão remota com o comando:

##### 3.2.3.1. Linux

``` sh
$ git flow release track RELEASE
```

##### 3.2.3.2. Windows Sourcetree

![Obter funcionalidade](obterFeatureSourcetree.png)


#### 3.2.4. Finalizar uma versão
A finalização de uma versão é um dos grandes passos na ramificação/branching do git. Ele executa várias ações:

![Finalizar versão](end-release.png)

Mescla o branch da versão no 'master'
Etiqueta a versão com seu nome
Mescla o branch da versão de volta no 'develop'
Remove o branch da versão

##### 3.2.4.1. Linux

``` sh
$ git flow release finish RELEASE -m "ENTRE ESTAS ASPAS É NECESSÁRIO INSERIR UMA MSG PARA SER ASSOCIADA A TAG CRIADA"
```

##### 3.2.4.2. Windows Sourcetree

Para finalizar uma versão basta acionar o comando do Git Flow, ir em "Outra Ação" e "Finalizar Release":

![Finalizar funcionalidade](finalizarReleaseSourcetree.png)


### 3.3. Hotfixes
Os hotfixes surgem da necessidade de agir imediatamente sobre uma situação indesejada na versão de produção ativa.
Pode ser criado a partir da tag correspondente no branch master que indica a versão em produção.

#### 3.3.1. Começar um hotfix

![Começar um hotfix](start-hotfix.png)

##### 3.3.1.1 Linux

Assim como os outros comandos do git flow, um hotfix inicia com

``` sh
$ git flow hotfix start RELEASE
```
O argumento RELEASE nesse caso marca a versão defeituosa na produção

##### 3.3.1.2 Windows Sourcetree

Para começar o conserto de um defeito no Sourcetree;
Acione o botão Git Flow:

![Nova hotfix](novoHotfixSourcetree.png)

Podemos criar o conserto para defeitos no master ou em casos que seja necessário criar a partir de um commit também é possível, sendo necessário somente selecionar a partir de qual commit a versão deve ser criada. Atribuir um nome conforme padrão do projeto.

![Nova hotfix 2](novoHotfix2Sourcetree.png)



#### 3.3.2. Finalizar um hotfix
![Finalizar um hotfix](end-hotfix.png)

Ao finalizar um hotfix ele é mesclado tanto no develop quanto no master. Além disso, o merge no master é etiquetado.

##### 3.3.2.1. Linux

``` sh
$ git flow hotfix finish RELEASE -m "ENTRE ESTAS ASPAS É NECESSÁRIO INSERIR UMA MSG PARA SER ASSOCIADA A TAG CRIADA"
```

##### 3.3.2.2. Windows Sourcetree

Para finalizar a correção do defeito basta acionar o comando do Git Flow, ir em "Outra Ação" e "Finalizar Conserto":

![Finalizar conserto](finalizarHotfixSourcetree.png)

![Finalizar conserto](finalizarHotfix2Sourcetree.png)

Para maiores informações sobre os fluxos do Git Flow utilizando o Sourcetree [clique aqui](https://blog.sourcetreeapp.com/2012/08/01/smart-branching-with-sourcetree-and-git-flow/).
