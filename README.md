
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
2. Instalar DependênciasO projeto requer apenas Flask e Pandas no ambiente Python.Bashpip install flask pandas
3. Executar o Servidor BackendInicie o servidor Flask:Bashpython app.py
4. Acessar no NavegadorAbra a seguinte URL no seu navegador para ver a interface:[http://127.0.0.1:5000](http://127.0.0.1:5000)
⚙️ Estrutura e Endpoints da APIEstrutura do Projeto/
├── app.py                 # API + Lógica do Backend
├── disciplinas.json       # Estrutura curricular do curso (dados estáticos)
├── notas.json             # Base de dados dinâmica (notas dos alunos)
├── index.html             # Frontend único (SPA com React)
└── README.md              # Documentação
Endpoints da APIMétodoEndpointFunçãoDados de Exemplo (Corpo)GET/Retorna a interface web principal (index.html).N/AGET/api/dadosRetorna o JSON completo com Disciplinas, Notas, Médias e Situação final para o Dashboard.N/APOST/api/atualizarRecebe e persiste a atualização de uma única nota no notas.json.{"codigo": "BSI0001", "campo": "n1", "valor": 8.5}GET/exportar_csvGera o boletim acadêmico completo e dispara o download em formato CSV.N/A🧠 Lógica de Negócio📘 Cálculo da MédiaA média é calculada com base nas três notas padrão:$$\text{Média} = \frac{\text{n1} + \text{n2} + \text{n3}}{3}$$🔁 Regra da RecuperaçãoA recuperação (REC) só é aplicada se:A nota de recuperação (REC) for maior que a menor nota anterior (n1, n2 ou n3).Se a condição for verdadeira, a REC substitui a menor nota original.A média final é recalculada com a nota substituída.🏁 Situação FinalA situação é determinada com base na média final, após a aplicação da regra de recuperação.SituaçãoRegra🟢 APROVADO$\text{Média} \ge 6.0$🔴 REPROVADO$\text{Média} < 6.0$🟡 CURSANDONotas incompletas (Falta n1, n2, ou n3, ou o campo $\text{REC}$ não foi preenchido quando necessário).⚪ PENDENTENenhum lançamento de nota (todos os campos de nota estão vazios/zero).🤝 Como ContribuirSua contribuição é muito bem-vinda! Siga o fluxo padrão do GitHub:Faça um Fork do projeto.Crie sua Feature Branch:Bashgit checkout -b feature/NovaFuncionalidade
Commit suas Mudanças:Bashgit commit -m "Adiciona nova funcionalidade"
Push para a Branch:Bashgit push origin feature/NovaFuncionalidade
Abra um Pull Request 💡📄 LicençaDistribuído sob a licença MIT. Para mais detalhes, consulte o arquivo LICENSE.
