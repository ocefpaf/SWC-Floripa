---
title: Instalando o ambiente conda para o SWC
layout: base
---

# Instalando o ambiente conda para o SWC

Recomendamos a distribuição Python gratuita
[Miniconda](http://conda.pydata.org/miniconda.html),
é uma versão mais leve da [Anaconda Scientific Python Distribution](https://store.continuum.io/cshop/anaconda/).
Apesar da distribuição Anaconda também funcionar
é muito mais rápido instalar o Miniconda,
e depois instalar os pacotes que necessita.
Se, por alguma razão precisar da distribuição Anaconda completa,
você pode digitar  `conda install anaconda` e instalar todos os pacotes.

## Instalação

Faça o download e instale a versão apropriada do Miniconda da URL [http://conda.pydata.org/miniconda.html](http://conda.pydata.org/miniconda.html).
Com o `conda` é possível criar ambientes que utilizam qualquer versão do Python
(e.x.: Python 2.7 ou Python 3.6),
então recomendamos instalar o último Python 3.x disponível e,
se depois você precisar de um ambiente com Python 2.7,
você pode criar um.
Usuários Windows também devem escolher entre versões 32-bit (Windows XP antigos) ou 64-bit (Windows modernos).

### Windows

Execute o instalador e escolha
*Just Me* (not *All Users*),
e instale em um diretório que tenha acesso.

Na tela "Advanced Installation Options",
deixe as caixas selecionadas se deseja que o Python do Miniconda seja o seu Python
*default*.

### Linux/OS X

Copie e cole as seguintes linhas:

```shell
if [[ $(uname) == "Darwin" ]]; then
  url=https://repo.continuum.io/miniconda/Miniconda3-latest-MacOSX-x86_64.sh
elif [[ $(uname) == "Linux" ]]; then
  url=https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
fi
curl $url -o miniconda.sh
bash miniconda.sh -b
```

## Criando o ambiente para o Workshop

Faça o download do aquivo [environment.yml](https://raw.githubusercontent.com/ocefpaf/SWC-Floripa/gh-pages/environment.yml),
usando o "left-click" do mouse e escolhendo `save as...`,
ou, no `OS X` e `Linux`, use esses comandos:

```bash
url=https://raw.githubusercontent.com/ocefpaf/SWC-Floripa/gh-pages/environment.yml
curl $url -o environment.yml
```

Depois, de dentro do diretório onde salvou o arquivo acima,
digite o seguinte commando na janela do terminal:

```bash
conda env create --name SWC --file environment.yml
```

Quando o ambiente terminar de instalar podemos ativá-lo digitando:

```bash
conda activate SWC
```

Para sair do ambiente devemos digitar

```bash
conda deactivate
```
