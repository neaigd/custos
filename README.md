<div align="center">
    <img src="https://github.com/p31x070/fact_chek/raw/main/LogoNIAD.png" alt="NIAD Logo" height="200">
</div>

# Custos - Custódia e Organização de Documentos

<div align="center">
    <img src="https://github.com/neaigd/custos/raw/main/modelagem_custus.png" alt="Diagrama Flowchart" height="700">
</div>

## Descrição

Este projeto tem como objetivo automatizar o processamento de documentos digitais (imagens, PDFs, arquivos de áudio, planilhas, documentos de texto, ZIPs) recebidos via WhatsApp e Gmail, garantindo a integridade e autenticidade das evidências para análises e processos judiciais.

O sistema extrai metadados, renomeia os arquivos seguindo um padrão, organiza em pastas, gera hashes (SHA-256) e cria uma folha de rosto com informações relevantes para a cadeia de custódia. Ele também visa incorporar conceitos do aplicativo "ProofMode" para reforçar a integridade dos documentos.

Este projeto se baseia nas diretrizes da norma **ABNT NBR ISO/IEC 27037:2013 - Tecnologia da informação — Técnicas de segurança — Diretrizes para identificação, coleta, aquisição e preservação de evidência digital**. Uma cópia da norma está incluída neste repositório para referência.

## Funcionalidades

*   **Renomeação Padronizada:** Automatiza a renomeação de arquivos recebidos, seguindo um padrão consistente.
*   **Extração de Metadados:** Extrai informações como data de criação/recebimento, tipo de arquivo e conteúdo relevante.
*   **Cálculo de Hash:** Gera hashes (SHA-256) dos arquivos originais para garantir a integridade.
*   **Organização em Pastas:** Organiza os arquivos em uma estrutura de pastas lógica e consistente.
*   **Tabela de Referência:** Cria uma tabela de referência (CSV ou SQLite) com informações sobre os arquivos originais, renomeados, hashes, etc.
*   **Folha de Rosto Automatizada:** Gera automaticamente uma folha de rosto para cada arquivo, contendo informações relevantes para a cadeia de custódia.
*   **Preparação para OTS:** Prepara os dados (arquivos, tabela de referência) para serem submetidos ao módulo OTS existente.
*   **Padrão de Citação:** Cria um padrão de citação para uso em documentos judiciais, incluindo hash ou referência à tabela.
*   **Escalabilidade:** Projetado para ser facilmente expandido para lidar com novos tipos de arquivos e necessidades futuras.
*   **Replicabilidade:** Garante que o processo seja totalmente replicável para diferentes casos e operadores.

## Tecnologias

*   **Linguagem:** Python
*   **Bibliotecas:**
    *   Pillow
    *   exifread
    *   PyPDF2
    *   mutagen
    *   openpyxl
    *   pandas
    *   fpdf2
    *   watchdog

## Instalação

1.  Clone o repositório:

    ```bash
    git clone [URL do seu repositório]
    ```

2.  Navegue até o diretório do projeto:

    ```bash
    cd custos
    ```

3.  Crie um ambiente virtual:

    ```bash
    python3 -m venv .venv
    ```

4.  Ative o ambiente virtual:

    ```bash
    source .venv/bin/activate   # (Linux/macOS)
    .venv\Scripts\activate  # (Windows)
    ```

5.  Instale as dependências:

    ```bash
    uv pip install Pillow exifread PyPDF2 mutagen openpyxl pandas fpdf2 watchdog
    ```

## Uso

1.  Execute o script `Renomear.py` (exemplo):

    ```bash
    python3 Renomear.py /caminho/do/seu/arquivo.pdf "NomeDoCliente" "TipoDoDocumento"
    ```

    *Substitua os valores entre aspas pelos valores correspondentes.*

## Estrutura de Pastas

Custodia/
YYYYMMDD_Cliente/
ArquivoRenomeado.ext
ArquivoOriginal.ext


## Tabela de Referência

O arquivo `referencias.csv` conterá as seguintes colunas:

*   Nome Original
*   Nome Renomeado
*   Data de Criação
*   Tipo de Documento
*   Hash Original (SHA-256)
*   Pasta
*   Comentários

## TODO

*   [ ] Implementar extração de metadados para diferentes tipos de arquivos.
*   [ ] Implementar a lógica de geração de nomes padronizados com números sequenciais.
*   [ ] Criar a folha de rosto em PDF.
*   [ ] Implementar o monitoramento automático de pastas.
*   [ ] Integrar com o módulo OTS para certificação de tempo na blockchain.
*   [ ] Implementar um padrão de citação para uso em documentos judiciais.
*   [ ] Pesquisar sobre a iniciativa C2PA e a viabilidade de integrar o suporte ao C2PA no script.
*   [ ] Criar testes unitários.
*   [ ] Implementar tratamento de erros robusto.

## Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e pull requests.

## Licença

[Adicione a licença do seu projeto]
