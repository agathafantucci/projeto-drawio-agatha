# projeto-drawio-agatha
## **Projeto Drawio - Agatha Fantucci**

Este projeto tem como objetivo representar, através de um diagrama criado no Draw.io, o fluxo de envio, processamento, armazenamento e arquivamento de arquivos em um ambiente de computação em nuvem utilizando serviços da AWS.

## Caminho do Arquivo no Sistema:

**1 - Actor (Usuário Final)**

O processo inicia com o usuário, que realiza o envio de um arquivo através da aplicação web ERP.

**2 - Aplicação Web – ERP (EC2 M5)**

A aplicação, hospedada em uma instância EC2 da família M5, recebe o arquivo enviado pelo usuário.
Essa camada é responsável por disponibilizar a interface de envio e por encaminhar os dados para os próximos serviços.

**3 - Lambda – Python**

Após o envio, a aplicação aciona uma função Lambda escrita em Python.
O Lambda atua como processador e orquestrador, recebendo a solicitação da aplicação e executando regras de negócio, validações ou transformações no arquivo antes de armazená-lo.

**4 - Banco de Dados – PostgreSQL**

O Lambda se comunica com o PostgreSQL, onde ficam armazenadas as informações estruturadas relacionadas ao arquivo (metadados, registros transacionais, ou dados complementares).
Aqui, a responsabilidade é de armazenar de forma organizada e persistente os dados necessários para a aplicação.

**5 - Amazon S3 Standard**

O backup dos arquivos é realizado no S3 Standard, garantindo armazenamento seguro e alta disponibilidade.
Esta camada serve como repositório primário de arquivos, com acesso rápido e redundância.

**6 - Amazon S3 Glacier**

Como etapa final, os arquivos armazenados no S3 Standard podem ser movidos para o S3 Glacier.
O Glacier tem como responsabilidade o armazenamento de longo prazo e de baixo custo, sendo ideal para arquivos que não precisam de acesso frequente, mas devem ser mantidos para auditoria ou recuperação futura.


<img width="725" height="415" alt="projeto_drawio drawio" src="https://github.com/user-attachments/assets/5d70ef76-eac9-4332-8adc-519af7499088" />
