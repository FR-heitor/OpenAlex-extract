# 📊 Extrator Bibliométrico OpenAlex - Versão Aberta para PPGs

Um aplicativo de código aberto desenvolvido em Python com interface gráfica (Tkinter) para automatizar a coleta, organização e análise de dados bibliométricos de docentes de Programas de Pós-Graduação (PPGs). 

A ferramenta consome dados da API gratuita do **OpenAlex** e gera um relatório completo em formato Excel (`.xlsx`), desenhado especificamente para auxiliar no preenchimento de relatórios da **CAPES (Plataforma Sucupira)**.

---

## 👨‍🔬 Autoria e Filiação
* **Autor:** Prof. Dr. Heitor Franco Santos
* **Filiação:** Universidade Federal de Sergipe (UFS)
* **Departamento:** Departamento de Fisiologia
* **Programa:** Programa de Pós-graduação em Ciências Naturais (PPGCN)

---

## ✨ Principais Funcionalidades

* **Busca Inteligente (Regex):** Insira uma lista mista de Nomes Completos, ORCIDs (ex: `0000-0002-...`) ou IDs do OpenAlex. O sistema identifica e padroniza a busca automaticamente, priorizando o ORCID para 100% de precisão.
* **Filtro Temporal Dinâmico:** Calcula e extrai automaticamente a produção dos últimos 5 anos completos mais o ano vigente.
* **Múltiplas Categorias:** Separa a produção científica em Artigos, Livros, Capítulos de Livros, Anais (Proceedings), Patentes e Preprints.
* **Geração de Referências:** Cria automaticamente a referência bibliográfica da obra (aproximação do padrão APA).
* **Análise de Coautoria (Grafo e Rede):** 
  * Identifica cruzamentos de obras entre os docentes da lista inserida.
  * Gera um **Grafo de Rede** em imagem (via `NetworkX` e `Matplotlib`) inserido automaticamente na aba de resumo do Excel.
* **Identificação de Discentes/Afiliados:** Através de filtros de afiliação (ex: "Universidade Federal de Sergipe" e "Ciências Naturais"), o robô varre os coautores de cada artigo para tentar identificar alunos vinculados ao PPG.
* **Tabela Padrão CAPES:** Insere no rodapé de cada pesquisador a estrutura oficial da tabela de Atividades Docentes pronta para preenchimento de dados locais (Bancas, Orientações, Carga horária).
* **IA e Citações:** Utiliza a IA do OpenAlex para inferir a principal área de atuação do docente e traz o número global de citações e variações de nome.

---

## 🚀 Como Instalar e Rodar

### Pré-requisitos
Certifique-se de ter o [Python 3.8+](https://www.python.org/downloads/) instalado no seu computador.

### Passo 1: Clone o repositório
```bash
git clone https://github.com/SEU-USUARIO/nome-do-repositorio.git
cd nome-do-repositorio
```

### Passo 2: Instale as dependências
Abra o terminal/prompt de comando na pasta do projeto e instale as bibliotecas necessárias:
```bash
pip install requests openpyxl matplotlib networkx
```
*(Nota: A biblioteca `tkinter` já vem embutida na maioria das instalações padrão do Python).*

### Passo 3: Execute o aplicativo
```bash
python extrator_aberto.py
```

---

## 📦 Como compilar um Executável Independente (.exe)
Se desejar distribuir o aplicativo para outros coordenadores ou secretários sem que eles precisem instalar o Python, utilize o **PyInstaller**:

1. Instale o PyInstaller:
   ```bash
   pip install pyinstaller
   ```
2. Gere o executável (esse processo esconde o terminal e cria um único arquivo `.exe`):
   ```bash
   pyinstaller --onefile --windowed extrator_aberto.py
   ```
3. O arquivo final estará na pasta `dist/`.

---

## 💡 Como Usar

1. Ao abrir o aplicativo, insira a lista de docentes na caixa de texto principal (um por linha). Recomenda-se colar o **ORCID** para evitar ambiguidades com nomes homônimos.
2. (Opcional) Nos campos de Filtro Institucional, insira a palavra-chave da universidade (ex: `UFS`) e do programa (ex: `Ciências Naturais`) para rastrear discentes e afiliados nas publicações.
3. Clique em **"Iniciar Extração Completa"**. O robô processará os dados na nuvem (sem travar a sua interface).
4. Ao final da extração, clique em **"Exportar Planilha Excel (.xlsx)"**, escolha o local de salvamento e abra o seu novo Dashboard Bibliométrico!

---

## ⚠️ Limitações Conhecidas (Lattes vs OpenAlex)
É importante ressaltar que bases de dados internacionais de indexação científica (OpenAlex, Scopus, Web of Science) rastreiam literatura publicada (documentos com DOI, ISSN, ISBN). 
**Atividades administrativas e acadêmicas, como participação em bancas, orientações concluídas e projetos financiados sem publicação atrelada, não existem nessas bases.** 
Por esse motivo, o aplicativo gera a tabela "X. ATIVIDADE DOCENTE" estruturada no Excel, porém com os campos administrativos em branco, aguardando o preenchimento manual ou o cruzamento com dados internos do PPG/Sucupira.

---

## 📄 Licença
Este projeto é distribuído sob a licença GNU - veja o arquivo [LICENSE](LICENSE) para mais detalhes. Versão aberta para uso livre pela comunidade acadêmica brasileira.
