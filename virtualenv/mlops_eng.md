# Projetos MLFlow

Este repositório faz parte do MLOps com exemplos práticos para aplicar diferentes técnicas do MLFlow e entender melhor seus componentes.

## Criando um Projeto MLFlow

Saiba mais sobre como criar um projeto MLFlow com Conda, uma solução de empacotamento que pode trabalhar com Python e outras dependências de sistema.

Para este projeto, usaremos um arquivo Parquet com dados sobre corridas de táxis de Nova York, chamado [{color}_tripdata_{year}-{month}.parquet]({color}_tripdata_{year}-{month}.parquet).

### Passo 1: Comece pelas dependências

Antes de entrar nos detalhes do projeto, provavelmente você já tem uma boa ideia do que precisa instalar. Recomendo configurar um ambiente Conda primeiro. Mesmo que prefira usar `pip` para instalar dependências, ainda é possível definir isso em um ambiente Conda.

Neste início do ciclo de vida do projeto, provavelmente você ainda não está pronto para treinar modelos, então vamos focar apenas no trabalho exploratório com o conjunto de dados.

```
conda create --name mlops_eng python=3.12.9
```

Depois que o ambiente for criado, ative-o para que os pacotes sejam instalados nesse ambiente ativado.

```
conda activate mlops_eng
```

Em seguida, com o ambiente _mlops_eng_ ativado, exporte as dependências para um novo arquivo YAML chamado _conda_env.yml_:

```
conda env export --name mlops_eng > mlops_eng.yml
```

Obtemos um arquivo semelhante a este:

```yaml
name: mlops_eng
channels:
  - defaults
  - https://repo.anaconda.com/pkgs/main
  - https://repo.anaconda.com/pkgs/r
dependencies:
  - python=3.12.9
  - pip
  - setuptools
  - wheel
```

Depois, adicione algumas linhas para usar o `pip` e instalar `mlflow` e `pandas`. Isso não é um requisito obrigatório, mas é útil saber que você pode usar o arquivo de ambiente Conda para adicionar mais dependências usando `pip` e não apenas `conda`. As linhas adicionadas devem ser assim:

```yaml

-  pip:
    - mlflow>=3.0.0rc0 --pre
    - ipykernel==6.29.5 
    - pydantic_settings==2.5.2
    - pandas==2.2.3  
    - tqdm==4.67.1
    - pyarrow==18.1.0
    - fastparquet==2024.11.0
```

O arquivo completo deve ficar exatamente como [`mlops_eng.yml`](mlops_eng.yml).

Como você adicionou as instalações do `pip` diretamente no arquivo, elas ainda não foram realmente instaladas, então execute o comando abaixo para garantir que tudo está funcionando:

```
conda env update --file mlops_eng.yml --prune
```

O comando irá verificar por novas (ou diferentes) dependências e instalá-las. A flag `--prune` remove qualquer coisa que não esteja mais definida no arquivo _mlops_eng.yml_. Neste caso, nada foi removido, mas é uma boa prática continuar usando essa opção.