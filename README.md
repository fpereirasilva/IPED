# IPED - Ferramenta de Forense Digital

O IPED é um software de código aberto que pode ser utilizado para processar e analisar evidências digitais, frequentemente apreendidas em cenas de crime por forças policiais ou em investigações corporativas por peritos particulares.

## Histórico

IPED - Indexador e Processador de Evidências Digitais é uma ferramenta implementada em Java, originalmente desenvolvida e ainda mantida por peritos em forense digital da Polícia Federal do Brasil desde 2012. Embora sempre tenha sido de código aberto, apenas em 2019 seu código foi oficialmente publicado.

Desde o início, o objetivo da ferramenta foi o processamento eficiente de dados e estabilidade. Algumas características-chave da ferramenta são:

- Processamento de dados por linha de comando para criação de casos em lote
- Suporte multiplataforma, testado em sistemas Windows e Linux
- Casos portáteis sem instalação, é possível executá-los a partir de mídias removíveis
- Interface de análise integrada e intuitiva
- Alto desempenho multithread e suporte a grandes casos: até 400GB/h de velocidade de processamento com hardware moderno e 135 milhões de itens em um (multi) caso, conforme registrado em 12/12/2019

Atualmente o IPED utiliza a [Biblioteca Sleuthkit](https://github.com/sleuthkit/sleuthkit) apenas para decodificar imagens de disco e sistemas de arquivos, portanto os mesmos formatos de imagem são suportados: RAW/DD, E01, ISO9660, AFF, VHD, VMDK. Também há suporte para os formatos EX01, VHDX, UDF(ISO), AD1 (AccessData) e UFDR (Cellebrite).

Se você é novo na ferramenta, por favor consulte o [Guia de Início para Iniciantes](https://github.com/lfcnassif/IPED/wiki/Beginner's-Start-Guide).

## Compilação

Para compilar a partir do código-fonte, você precisa ter git, maven e Java JDK 11 + JavaFX (ex: Liberica OpenJDK 11 Full JDK) instalados. Defina a variável de ambiente JAVA_HOME para a pasta de instalação do Java 11 e execute:
```
git clone https://github.com/sepinf-inc/IPED.git
cd IPED
mvn clean install
```
Isso irá gerar uma versão snapshot do IPED na pasta target/release.

<b>Atenção:</b> a branch master padrão é a de desenvolvimento e é instável. Se você deseja compilar uma versão estável, faça checkout em uma das tags de release após a etapa de clone.

No Linux, você também precisa compilar o The Sleuthkit e dependências adicionais. Por favor consulte a [Seção Linux](https://github.com/sepinf-inc/IPED/wiki/Linux)

Contribuições são muito bem-vindas! Antes de contribuir, por favor consulte [Contribuindo](https://github.com/lfcnassif/IPED/wiki/Contributing)

## Funcionalidades

Algumas das diversas funcionalidades do IPED estão listadas abaixo:

- Hashes suportados: md5, sha-1, sha-256, sha-512 e edonkey. PhotoDNA também está disponível **para forças policiais** (entre em contato via iped arroba pf ponto gov ponto br)
- Conjuntos de hashes suportados: NIST NSRL, NIST CAID, ProjectVIC, Interpol ICSE, formato CSV padrão
- Deduplicação rápida por hash
- Análise de assinaturas
- Categorização por tipo de arquivo e propriedades
- Expansão recursiva de contêineres de dezenas de formatos de arquivo
- Expansão de discos forenses/virtuais embutidos: suporta DD segmentado ou único, E01, EX01, VHD, VHDX, VMDK (VMDKs diferenciais também são suportados)
- Galeria de imagens e vídeos para centenas de formatos
- Georreferenciamento de dados GPS, utilizando Google Maps, Bing ou OpenStreetMaps
- Buscas por expressões regulares com validação opcional por script para cartões de crédito, e-mails, URLs, endereços IP e MAC, valores monetários, carteiras de bitcoin, ethereum, monero, ripple e mais...
- Visualizadores embutidos para hexadecimal, texto unicode, metadados e formato nativo
- Indexação e busca rápida de conteúdo e metadados de arquivos, incluindo arquivos desconhecidos e espaço não alocado
- Motor eficiente de data carving (utiliza < 10% do tempo de processamento) que varre muito mais do que o espaço não alocado, com suporte a +40 formatos de arquivo, incluindo vídeos, extensível por scripting
- Reconhecimento Óptico de Caracteres (OCR) com tecnologia Tesseract 5
- Detecção de criptografia para formatos conhecidos e usando teste de entropia
- Perfis de processamento: forense, pedo (csam), triagem, modo rápido (prévia) e cego (para extração automática de dados)
- Detecção de +70 idiomas
- Reconhecimento de Entidades Nomeadas (necessita dos modelos Stanford CoreNLP para download)
- Filtros personalizáveis baseados em qualquer metadado de arquivo
- Busca de documentos similares com limiar configurável
- Busca de imagens similares, usando imagem interna ou externa
- Reconhecimento de faces similares, otimizado para executar sem GPU, com limiar configurável
- Visualização unificada de timeline em tabela e filtragem de eventos para análise de linha do tempo
- Agrupamento (clustering) poderoso de arquivos baseado em QUALQUER metadado
- Suporte a multicasos com até 135 milhões de itens
- Extensível com scripts em JavaScript e Python (incluindo extensões cpython)
- Integração com ferramentas de linha de comando externas para decodificação de arquivos
- Histórico de navegadores para IE, Edge, Firefox, Chrome e Safari
- Parsers personalizados para Emule, Shareaza, Ares, WhatsApp, Skype, Telegram, BitTorrent, ActivitiesCache e mais...
- Detecção rápida de nudez em imagens e vídeos usando algoritmo de florestas aleatórias (agradecimentos ao autor @tc-wleite)
- Detecção de nudez usando modelo de deep learning Yahoo open-nsfw (necessita keras e tensorflow)
- Transcrição de áudio, implementações locais e remotas com serviços Azure e Google Cloud
- Análise de grafos para comunicações (chamadas, e-mails, mensagens instantâneas...)
- Processamento estável com decodificação de sistema de arquivos e parsing de arquivos em processos separados
- Retomada ou reinício de processamento parado ou abortado (opções --continue/--restart)
- API Web para pesquisa em casos remotos, obtenção de metadados de arquivos, conteúdo bruto, texto decodificado, miniaturas e postagem de marcadores
- Criação de marcadores/tags para dados de interesse
- Relatórios em HTML, CSV e casos portáteis com dados marcados

## Capturas de Tela

Processamento:
![imagem](https://github.com/sepinf-inc/IPED/assets/7276994/bf29b44a-a924-4c65-845c-6282a4b91861)

Análise:
![imagem](https://github.com/sepinf-inc/IPED/assets/7276994/5fca2b65-6763-4bc1-9284-604c8b325d54)

Data Carving e Miniaturas de Vídeo:
![imagem](https://github.com/sepinf-inc/IPED/assets/7276994/4d908fe5-6cb1-443b-96fa-d937fa1d2e2d)

Resultados de Expressões Regulares:
![imagem](https://github.com/sepinf-inc/IPED/assets/7276994/db34adc7-d7b9-4b56-8a35-99e095380d0b)

Mapa:
![imagem](https://github.com/sepinf-inc/IPED/assets/7276994/279b9280-3a72-484a-8aed-e4d015df196f)

Vínculos de comunicação:
![imagem](https://github.com/sepinf-inc/IPED/assets/7276994/8b164948-fa36-47b8-a249-f64547a36b28)

Busca de faces:
![imagem](https://github.com/sepinf-inc/IPED/assets/7276994/d9b37060-afa4-4e9b-ae55-a9d8413ac43a)

Transcrição de Áudio:
![imagem](https://github.com/sepinf-inc/IPED/assets/7276994/ebded2ad-f88d-43c8-9699-66e498c9939c)

Linha do Tempo:
![imagem](https://github.com/sepinf-inc/IPED/assets/7276994/011657e3-8ff2-4105-b3c2-116980772fc0)

Gráfico Temporal:
![imagem](https://github.com/sepinf-inc/IPED/assets/7276994/81df1c18-361d-49f1-b755-36520437803a)

Correlação de eventos de 2 suspeitos e atividades ilegais:
![imagem](https://github.com/sepinf-inc/IPED/assets/7276994/e1f47b15-ba89-4436-9291-7ec354ef2b57)
