# 🎓 Sistema de Controle Acadêmico – BSI

## 💻 Visão Geral do Projeto

Um **sistema web completo** desenvolvido para o curso de **Bacharelado em Sistemas de Informação (BSI)**, focado em gerenciamento ágil de notas e acompanhamento acadêmico. Este projeto utiliza uma **arquitetura moderna** com **Backend em Python/Flask** e **Frontend em React (SPA)**, destacando-se pela atualização instantânea dos dados e persistência simplificada em arquivos JSON. Ideal para demonstrar proficiência em full-stack web development e manipulação de dados em tempo real. 



[Image of a dashboard with interactive charts and KPI's]


---

## ✨ Destaques & Funcionalidades Principais

| Ícone | Destaque | Descrição |
| :---: | :--- | :--- |
| 📊 | **Dashboard Interativo** | KPIs (Aprovadas, Reprovadas, Cursando, Pendentes) e gráficos animados (Recharts) para uma visualização rápida do progresso. |
| ✏️ | **Edição em Tempo Real** | Altere notas diretamente na tabela. A média é **recalculada imediatamente** e o arquivo `notas.json` é **atualizado na hora**. |
| 🧠 | **Lógica Inteligente de REC** | Implementação de uma regra de recuperação que **substitui automaticamente a menor nota** apenas se a nota de recuperação for superior a ela. |
| 📁 | **Exportação de Boletim** | Geração e download de um boletim completo em formato **CSV**, compatível com Excel, Google Sheets e LibreOffice. |
| 🌙 | **Interface Moderna** | Design limpo, responsivo e com suporte a **Dark Mode** (TailwindCSS) para uma melhor experiência do usuário. |
| 🗃️ | **Persistência Simples (JSON)** | Sem a complexidade de um banco de dados SQL. Os dados são salvos em `disciplinas.json` e `notas.json`. |

---

## 🛠️ Tecnologias Utilizadas

| Camada | Tecnologias | Descrição |
| :---: | :--- | :--- |
| **Backend** | **Python, Flask, Pandas** | Python como linguagem principal; Flask para a API leve; Pandas para o processamento e gerenciamento eficiente dos dados. |
| **Frontend** | **React (CDN), TailwindCSS** | Frontend como Single Page Application (SPA); React para componentes dinâmicos; TailwindCSS para estilização utilitária e moderna. |
| **Visualização** | **Recharts, Lucide Icons** | Recharts para gráficos interativos; Lucide Icons para ícones modernos. |
| **Dados** | **JSON** | Armazenamento persistente e simples dos dados acadêmicos. |

---

## 🚀 Como Executar Localmente

Siga estes passos para configurar e executar o projeto em sua máquina.

### 1. Clonar o Repositório

```bash
git clone [https://github.com/FelipeMzero/Notas-Academicas.git](https://github.com/FelipeMzero/Notas-Academicas.git)
cd Notas-Academicas
```

### 2\. Instalar Dependências

O projeto requer apenas **Flask** e **Pandas** no ambiente Python.

```bash
pip install flask pandas
```

### 3\. Executar o Servidor Backend

Inicie o servidor Flask:

```bash
python app.py
```

### 4\. Acessar no Navegador

Abra a seguinte URL no seu navegador para ver a interface:

```
[http://127.0.0.1:5000](http://127.0.0.1:5000)
```

-----

## ⚙️ Estrutura e Endpoints da API

### Estrutura do Projeto

```
/
├── app.py                 # API + Lógica do Backend
├── disciplinas.json       # Estrutura curricular do curso (dados estáticos)
├── notas.json             # Base de dados dinâmica (notas dos alunos)
├── index.html             # Frontend único (SPA com React)
└── README.md              # Documentação
```

### Endpoints da API

| Método | Endpoint | Função | Dados de Exemplo (Corpo) |
| :---: | :--- | :--- | :--- |
| `GET` | `/` | Retorna a interface web principal (`index.html`). | N/A |
| `GET` | `/api/dados` | Retorna o JSON completo com **Disciplinas, Notas, Médias e Situação final** para o Dashboard. | N/A |
| `POST` | `/api/atualizar` | Recebe e persiste a atualização de uma única nota no `notas.json`. | `{"codigo": "BSI0001", "campo": "n1", "valor": 8.5}` |
| `GET` | `/exportar_csv` | Gera o boletim acadêmico completo e dispara o download em formato CSV. | N/A |

-----

## 🧠 Lógica de Negócio

### 📘 Cálculo da Média

A média é calculada com base nas três notas padrão:

$$\text{Média} = \frac{\text{n1} + \text{n2} + \text{n3}}{3}$$

### 🔁 Regra da Recuperação

A recuperação (`REC`) só é aplicada se:

1.  A nota de recuperação (`REC`) for **maior** que a menor nota anterior (n1, n2 ou n3).
2.  Se a condição for verdadeira, a `REC` **substitui** a menor nota original.
3.  A média final é recalculada com a nota substituída.

### 🏁 Situação Final

A situação é determinada com base na média final, após a aplicação da regra de recuperação.

| Situação | Regra |
| :---: | :--- |
| 🟢 **APROVADO** | $\text{Média} \ge 6.0$ |
| 🔴 **REPROVADO** | $\text{Média} < 6.0$ |
| 🟡 **CURSANDO** | Notas incompletas (Falta n1, n2, ou n3, ou o campo $\text{REC}$ não foi preenchido quando necessário). |
| ⚪ **PENDENTE** | Nenhum lançamento de nota (todos os campos de nota estão vazios/zero). |

-----

## 🤝 Como Contribuir

Sua contribuição é muito bem-vinda\! Siga o fluxo padrão do GitHub:

1.  **Faça um Fork** do projeto.
2.  **Crie sua Feature Branch:**
    ```bash
    git checkout -b feature/NovaFuncionalidade
    ```
3.  **Commit suas Mudanças:**
    ```bash
    git commit -m "Adiciona nova funcionalidade"
    ```
4.  **Push para a Branch:**
    ```bash
    git push origin feature/NovaFuncionalidade
    ```
5.  **Abra um Pull Request** 💡

-----

## 📄 Licença

Distribuído sob a licença **MIT**.

O texto da licença MIT completo geralmente reside no arquivo `LICENSE` no repositório, mas para referência rápida, segue o formato padrão:

```
MIT License

```

*Lembre-se de criar o arquivo `LICENSE` separado em seu repositório com o conteúdo acima, substituindo `[Ano]` e `[Seu Nome ou Nome da Organização]`.*
