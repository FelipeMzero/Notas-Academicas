🎓 Sistema de Controle Acadêmico BSI

Um sistema web completo para gerenciamento de notas e acompanhamento de desempenho acadêmico, focado no curso de Bacharelado em Sistemas de Informação (BSI). O projeto utiliza uma arquitetura leve com Python (Flask) no backend e React no frontend, garantindo persistência de dados em JSON e atualizações em tempo real.

📋 Funcionalidades Principais

Dashboard Interativo: Visão geral com gráficos e KPIs mostrando o progresso do curso (Disciplinas Aprovadas, Reprovadas, Cursando e Pendentes).

Gestão de Notas em Tempo Real: Edição direta na tabela. Ao alterar uma nota, o sistema recalcula a média e atualiza o arquivo notas.json instantaneamente.

Lógica de Recuperação Automática: O sistema identifica automaticamente se a nota de recuperação deve substituir a menor nota do semestre para o cálculo da média final.

Persistência em JSON: Todos os dados são salvos em arquivos locais (notas.json), eliminando a necessidade de configurar bancos de dados complexos.

Exportação de Relatórios: Funcionalidade para baixar o boletim completo em formato .csv (compatível com Excel).

Design Responsivo: Interface moderna e adaptável para desktop e dispositivos móveis (Dark Mode).

Auto-Refresh: O frontend sincroniza periodicamente com o backend para garantir que os dados estejam sempre atualizados.

🛠️ Tecnologias Utilizadas

Backend: Python, Flask, Pandas.

Frontend: HTML5, Tailwind CSS, React (via CDN), Babel (Standalone), Recharts (Gráficos), Lucide (Ícones).

Dados: JSON (Estrutura NoSQL simples).

🚀 Como Executar o Projeto

Pré-requisitos

Python 3.x instalado.

Pip (gerenciador de pacotes do Python).

Instalação

Clone o repositório:

git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
cd seu-repositorio


Instale as dependências:

pip install flask pandas


Execute o servidor:

python app.py


Acesse no navegador:
Abra http://127.0.0.1:5000 em seu navegador favorito.

📂 Estrutura de Arquivos

/
├── app.py                 # Servidor Flask (Lógica de Backend e API)
├── disciplinas.json       # Estrutura estática do currículo (Matérias, Semestres)
├── notas.json             # Banco de dados dinâmico (Salva as notas do aluno)
├── index.html             # Frontend Único (Single Page Application com React)
└── README.md              # Documentação do projeto


⚙️ Funcionalidades da API

O backend Flask expõe os seguintes endpoints:

GET /: Renderiza a aplicação web.

GET /api/dados: Retorna o JSON completo com disciplinas, notas e status calculados.

POST /api/atualizar: Recebe atualizações de notas (codigo, campo, valor) e salva no arquivo JSON.

GET /exportar_csv: Gera e baixa o arquivo CSV com o histórico atual.

🧠 Lógica de Negócio

O cálculo da situação do aluno segue as seguintes regras (configuradas em app.py):

Média: (N1 + N2 + N3) / 3.

Recuperação: Se houver nota de recuperação (rec > 0) e ela for maior que a menor das três notas parciais, ela substitui essa menor nota no cálculo da média.

Status:

APROVADO: Média ≥ 6.0.

REPROVADO: Média < 6.0 (após recuperação).

CURSANDO: Média parcial existe, mas o semestre não foi concluído (ex: falta N3).

PENDENTE: Nenhuma nota lançada.

🤝 Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues ou enviar pull requests.

Faça um Fork do projeto.

Crie sua Feature Branch (git checkout -b feature/NovaFuncionalidade).

Commit suas mudanças (git commit -m 'Adicionando nova funcionalidade').

Push para a Branch (git push origin feature/NovaFuncionalidade).

Abra um Pull Request.

📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo LICENSE para mais detalhes.
