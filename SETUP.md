
# Como montar o ambiente de desenvolvimento

## No Google Collab

No Google Collab disponivel aqui [https://colab.research.google.com/](https://colab.research.google.com/), o ambiente de desenvolvimento já vem pré-configurado com Python e as principais bibliotecas necessárias. Basta abrir os notebooks e selecionar o kernel apropriado.

## Num ambiente de desenvolvimento local

Certifique-se de ter a ferramenta `git` instalada e use o seguinte comando para clonar o repositório:

```shell
git clone https://github.com/adalves-ufabc/2026.Q3-PLN.git
```

Entre na pasta do repositório clonado com o comando:

```shell
cd 2026.Q3-PLN
```

> Vamos utilizar a seguir o Python 3.13 por padrão mas mantivemos compatibilidade com o Python 3.11 ou
posterior. São oferecidas diferentes formas de montar o ambiente de desenvolvimento, sendo a principal com `uv`, mas também é possível usar `Conda` ou `pip`.

### Com uv

Instale o `uv` a partir do site oficial [https://docs.astral.sh/uv/getting-started/installation/](https://docs.astral.sh/uv/getting-started/installation/)

Após a instalação, sincronize as dependências dos notebooks com o comando:

```shell
uv sync
```

### Com conda

Instale o Conda Forge a partir do site oficial [https://conda-forge.org/](https://conda-forge.org/)

Após instalar o Conda Forge, crie o ambiente a partir do arquivo [environment.yml](environment.yml) com o comando:

```shell
conda env create -f environment.yml
```

Ative o ambiente com o comando:

```shell
conda activate ufabc-2026-q3-pln
```

Este arquivo usa o canal conda-forge e instala Python 3.13 com as dependências dos notebooks.

### Com pip

Se não tiver `uv` ou Conda instalado, você pode usar `pip` para montar o ambiente diretamente sobre o python local.

Instale o Python 3.13, se ainda não estiver instalado do site oficial [https://www.python.org/downloads/](https://www.python.org/downloads/)

Consulte a versão instalada com o comando:

```shell
python --version
```

Crie o ambiente virtual como seguinte comando:

```powershell
py -3.13 -m venv .venv
```

```sh
python3.13 -m venv .venv
```

Se houver apenas uma versão do Python instalada e ela já for a desejada, você pode usar o comando:

```shell
python -m venv .venv
```

Ative o ambiente com o comando correspondente ao seu ambiente:

#### Windows

```bat
.venv\Scripts\activate.bat
```

#### Linux / macOS

```sh
source .venv/bin/activate
```

### Dependências

Atualize o `pip` com o comando:

```shell
python -m pip install --upgrade pip
```

Instale as dependências com o comando:

```shell
pip install -r requirements.txt
```

### Modelos do spaCy

Para executar notebooks que carregam modelos de português do spaCy, instale os
modelos usados nas aulas 5 e 6:

```shell
python -m spacy download pt_core_news_sm
python -m spacy download pt_core_news_lg
```

> Se estiver usando o `vscode`, abra os arquivos `.ipynb` e selecione o kernel do ambiente ativo por exemplo: `.venv` ou `ufabc-2026-q3-pln`.

> Os modelos do spaCy e os corpora do NLTK são recursos de runtime baixados fora do lock do `uv`, os notebooks baixam os corpora do NLTK em células próprias.
