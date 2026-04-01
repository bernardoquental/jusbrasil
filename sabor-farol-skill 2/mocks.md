# Dados Mock Realistas - Jusbrasil

Dados fictícios para uso em protótipos. Todos seguem formatos reais do sistema judiciário brasileiro.

---

## Processos Judiciais

### Processo 1 - Trabalhista
```json
{
  "numero_cnj": "0001234-56.2024.5.02.0001",
  "tribunal": "TRT-2",
  "vara": "1a Vara do Trabalho de Sao Paulo",
  "classe": "Reclamacao Trabalhista",
  "assunto": "Verbas Rescisorias",
  "distribuicao": "15/03/2024",
  "status": "Em andamento",
  "valor_causa": "R$ 45.000,00",
  "partes": {
    "autor": "Maria Fernanda Silva Santos",
    "cpf_autor": "321.654.987-00",
    "advogado_autor": "Dr. Ricardo Mendes (OAB/SP 234.567)",
    "reu": "Tech Solutions Ltda.",
    "cnpj_reu": "12.345.678/0001-90",
    "advogado_reu": "Dra. Camila Rocha (OAB/SP 345.678)"
  }
}
```

### Processo 2 - Civel
```json
{
  "numero_cnj": "1098765-43.2023.8.26.0100",
  "tribunal": "TJ-SP",
  "vara": "5a Vara Civel do Foro Central",
  "classe": "Procedimento Comum Civel",
  "assunto": "Indenizacao por Dano Moral",
  "distribuicao": "22/08/2023",
  "status": "Sentenca proferida",
  "valor_causa": "R$ 30.000,00",
  "partes": {
    "autor": "Joao Pedro Almeida",
    "cpf_autor": "123.456.789-00",
    "advogado_autor": "Dr. Felipe Andrade (OAB/SP 123.456)",
    "reu": "Banco Nacional S.A.",
    "cnpj_reu": "00.123.456/0001-00",
    "advogado_reu": "Dra. Ana Paula Costa (OAB/SP 456.789)"
  }
}
```

### Processo 3 - Consumidor
```json
{
  "numero_cnj": "0054321-12.2024.8.19.0001",
  "tribunal": "TJ-RJ",
  "vara": "3o Juizado Especial Civel",
  "classe": "Procedimento do Juizado Especial Civel",
  "assunto": "Inclusao Indevida em Cadastro de Inadimplentes",
  "distribuicao": "10/01/2024",
  "status": "Audiencia designada",
  "valor_causa": "R$ 15.000,00",
  "partes": {
    "autor": "Carolina Beatriz Ferreira",
    "cpf_autor": "987.654.321-00",
    "advogado_autor": null,
    "reu": "Operadora Telecom S.A.",
    "cnpj_reu": "33.000.167/0001-01"
  }
}
```

### Processo 4 - Familia
```json
{
  "numero_cnj": "0002468-80.2023.8.13.0024",
  "tribunal": "TJ-MG",
  "vara": "2a Vara de Familia de Belo Horizonte",
  "classe": "Divorcio Consensual",
  "assunto": "Divorcio - Partilha de Bens",
  "distribuicao": "05/06/2023",
  "status": "Transitado em julgado",
  "valor_causa": "R$ 500.000,00",
  "partes": {
    "autor": "Lucas Gabriel Martins",
    "cpf_autor": "456.789.123-00",
    "reu": "Patricia Souza Martins",
    "cpf_reu": "789.123.456-00"
  }
}
```

### Processo 5 - Tributario
```json
{
  "numero_cnj": "5001234-55.2024.4.03.6100",
  "tribunal": "TRF-3",
  "vara": "4a Vara Federal de Sao Paulo",
  "classe": "Mandado de Seguranca",
  "assunto": "Isencao de Imposto de Renda por Doenca Grave",
  "distribuicao": "20/02/2024",
  "status": "Aguardando decisao liminar",
  "valor_causa": "R$ 120.000,00",
  "partes": {
    "autor": "Roberto Carlos Oliveira",
    "cpf_autor": "654.321.987-00",
    "advogado_autor": "Dr. Andre Barbosa (OAB/SP 567.890)",
    "reu": "Uniao Federal - Receita Federal do Brasil"
  }
}
```

---

## Andamentos Processuais

```json
[
  {
    "data": "06/03/2025",
    "tipo": "Decisao",
    "descricao": "Proferida decisao. Vistos. Defiro o pedido de tutela antecipada para suspender a cobranca ate julgamento do merito.",
    "resumo_simplificado": "O juiz aceitou o pedido para parar a cobranca enquanto o processo continua."
  },
  {
    "data": "28/02/2025",
    "tipo": "Peticao",
    "descricao": "Juntada de peticao de manifestacao do autor.",
    "resumo_simplificado": "Seu advogado enviou um documento ao processo."
  },
  {
    "data": "15/02/2025",
    "tipo": "Audiencia",
    "descricao": "Realizada audiencia de conciliacao. As partes nao chegaram a acordo.",
    "resumo_simplificado": "Houve uma reuniao no tribunal para tentar um acordo, mas nao deu certo."
  },
  {
    "data": "01/02/2025",
    "tipo": "Citacao",
    "descricao": "Expedido mandado de citacao ao reu.",
    "resumo_simplificado": "A outra parte foi oficialmente comunicada sobre o processo."
  },
  {
    "data": "20/01/2025",
    "tipo": "Distribuicao",
    "descricao": "Distribuido por sorteio a 5a Vara Civel.",
    "resumo_simplificado": "O processo foi encaminhado para a vara que vai cuidar do caso."
  }
]
```

---

## Jurisprudencia

### Decisao 1 - STJ
```json
{
  "tribunal": "STJ",
  "orgao_julgador": "3a Turma",
  "recurso": "REsp 1.234.567/SP",
  "relator": "Min. Nancy Andrighi",
  "data_julgamento": "12/11/2024",
  "data_publicacao": "20/11/2024",
  "ementa": "RECURSO ESPECIAL. DIREITO DO CONSUMIDOR. INSCRICAO INDEVIDA EM CADASTRO DE INADIMPLENTES. DANO MORAL IN RE IPSA. VALOR DA INDENIZACAO. RAZOABILIDADE. 1. A inscricao indevida do nome do consumidor em cadastro de inadimplentes configura dano moral in re ipsa, dispensando a comprovacao de prejuizo concreto. 2. O valor da indenizacao deve ser fixado com razoabilidade, atendendo ao carater compensatorio e pedagogico. 3. Recurso especial parcialmente provido.",
  "decisao": "Por unanimidade, dar parcial provimento ao recurso especial para reduzir a indenizacao para R$ 10.000,00.",
  "assuntos": ["Dano Moral", "Cadastro de Inadimplentes", "Direito do Consumidor"]
}
```

### Decisao 2 - TJ-SP
```json
{
  "tribunal": "TJ-SP",
  "orgao_julgador": "12a Camara de Direito Privado",
  "recurso": "Apelacao Civel 1000234-56.2023.8.26.0100",
  "relator": "Des. Sandra Galhardo",
  "data_julgamento": "05/12/2024",
  "data_publicacao": "10/12/2024",
  "ementa": "APELACAO. LOCACAO. ACAO DE DESPEJO POR FALTA DE PAGAMENTO CUMULADA COM COBRANCA. PROCEDENCIA. INADIMPLENCIA COMPROVADA. RECURSO DESPROVIDO. 1. Comprovada a inadimplencia do locatario, correta a decretacao do despejo. 2. O locatario que nao purga a mora no prazo legal assume os riscos da rescisao contratual.",
  "decisao": "Negaram provimento ao recurso, por votacao unanime.",
  "assuntos": ["Locacao", "Despejo", "Inadimplencia"]
}
```

### Decisao 3 - TST
```json
{
  "tribunal": "TST",
  "orgao_julgador": "5a Turma",
  "recurso": "RR 10234-56.2022.5.02.0001",
  "relator": "Min. Douglas Alencar Rodrigues",
  "data_julgamento": "18/09/2024",
  "data_publicacao": "25/09/2024",
  "ementa": "RECURSO DE REVISTA. HORAS EXTRAS. CARGO DE CONFIANCA. ART. 62, II, DA CLT. NAO CONFIGURACAO. CONTROLE DE JORNADA. 1. O mero recebimento de gratificacao de funcao nao exclui o direito as horas extras se demonstrado o efetivo controle de jornada pelo empregador. 2. Recurso de revista conhecido e provido.",
  "decisao": "Conhecer do recurso de revista e dar-lhe provimento.",
  "assuntos": ["Horas Extras", "Cargo de Confianca", "Jornada de Trabalho"]
}
```

---

## Modelos de Peticao

```json
[
  {
    "titulo": "Peticao Inicial - Acao de Indenizacao por Danos Morais e Materiais",
    "categoria": "Civel",
    "subcategoria": "Responsabilidade Civil",
    "downloads": 12450,
    "avaliacao": 4.7,
    "formato": "DOCX",
    "autor": "Equipe Jusbrasil"
  },
  {
    "titulo": "Contestacao Trabalhista - Verbas Rescisorias",
    "categoria": "Trabalhista",
    "subcategoria": "Rescisao Contratual",
    "downloads": 8320,
    "avaliacao": 4.5,
    "formato": "DOCX",
    "autor": "Equipe Jusbrasil"
  },
  {
    "titulo": "Recurso de Apelacao Civel",
    "categoria": "Civel",
    "subcategoria": "Recursos",
    "downloads": 6780,
    "avaliacao": 4.8,
    "formato": "DOCX",
    "autor": "Equipe Jusbrasil"
  },
  {
    "titulo": "Habeas Corpus - Excesso de Prazo na Prisao Preventiva",
    "categoria": "Criminal",
    "subcategoria": "Liberdade Provisoria",
    "downloads": 3210,
    "avaliacao": 4.6,
    "formato": "DOCX",
    "autor": "Equipe Jusbrasil"
  },
  {
    "titulo": "Peticao de Divorcio Consensual Extrajudicial",
    "categoria": "Familia",
    "subcategoria": "Divorcio",
    "downloads": 15600,
    "avaliacao": 4.9,
    "formato": "DOCX",
    "autor": "Equipe Jusbrasil"
  },
  {
    "titulo": "Mandado de Seguranca contra Ato de Autoridade Publica",
    "categoria": "Administrativo",
    "subcategoria": "Mandado de Seguranca",
    "downloads": 4500,
    "avaliacao": 4.4,
    "formato": "DOCX",
    "autor": "Equipe Jusbrasil"
  }
]
```

---

## Conversas Advogado com Jus IA

### Conversa 1 - Pesquisa de tese
```json
[
  {
    "from": "user",
    "message": "Preciso de jurisprudencia do STJ sobre dano moral por inscricao indevida no SPC. Quero decisoes de 2024."
  },
  {
    "from": "assistant",
    "message": "Encontrei 47 decisoes do STJ sobre dano moral por inscricao indevida em cadastros de inadimplentes em 2024. Os principais entendimentos sao:\n\n1. **Dano moral in re ipsa**: A 3a e 4a Turmas mantem que a inscricao indevida gera dano moral presumido (REsp 1.234.567/SP).\n\n2. **Valores de indenizacao**: A faixa predominante em 2024 foi de R$ 5.000 a R$ 15.000, com media de R$ 10.000.\n\n3. **Excecao - devedor habitual**: Quando o consumidor ja possui outras inscricoes legitimas, aplica-se a Sumula 385/STJ, afastando a indenizacao.\n\nQuer que eu aprofunde algum desses pontos?",
    "sources": [
      {"type": "jurisprudencia", "ref": "REsp 1.234.567/SP", "verified": true},
      {"type": "sumula", "ref": "Sumula 385/STJ", "verified": true}
    ]
  },
  {
    "from": "user",
    "message": "Aprofunde o ponto 1. Preciso da fundamentacao completa para usar na minha peticao."
  },
  {
    "from": "assistant",
    "message": "## Dano moral in re ipsa por inscricao indevida\n\nA jurisprudencia consolidada do STJ reconhece que a inscricao indevida em cadastros de protecao ao credito (SPC/Serasa) configura dano moral presumido, independente de prova do prejuizo.\n\n### Fundamento legal\n- **Art. 5o, X, CF**: Direito a inviolabilidade da honra e imagem\n- **Art. 186 e 927, CC**: Responsabilidade civil por ato ilicito\n- **Art. 43, CDC**: Direitos do consumidor quanto a bancos de dados\n\n### Precedentes recentes (2024)\n\n> *\"A inscricao indevida do nome do consumidor em cadastro restritivo de credito configura dano moral in re ipsa, sendo desnecessaria a comprovacao de efetivo prejuizo.\"*\n> - REsp 1.234.567/SP, Rel. Min. Nancy Andrighi, 3a Turma, j. 12/11/2024\n\n> *\"O dano moral decorrente da inscricao indevida prescinde de prova, bastando a demonstracao do ato ilicito.\"*\n> - AgInt no AREsp 2.345.678/RJ, Rel. Min. Marco Buzzi, 4a Turma, j. 08/10/2024\n\nPosso criar um rascunho da fundamentacao para sua peticao?",
    "sources": [
      {"type": "jurisprudencia", "ref": "REsp 1.234.567/SP", "verified": true},
      {"type": "jurisprudencia", "ref": "AgInt no AREsp 2.345.678/RJ", "verified": true},
      {"type": "legislacao", "ref": "Art. 5o, X, CF", "verified": true},
      {"type": "legislacao", "ref": "Art. 43, CDC", "verified": true}
    ]
  }
]
```

### Conversa 2 - Criacao de peca
```json
[
  {
    "from": "user",
    "message": "Crie uma contestacao trabalhista. Meu cliente e uma empresa de tecnologia que demitiu um dev senior por justa causa (desídia). O ex-funcionario alega que nao houve advertencias previas."
  },
  {
    "from": "assistant",
    "message": "Vou criar a contestacao. Antes, preciso confirmar alguns pontos:\n\n1. **Advertencias documentadas**: A empresa tem registros de advertencias ou suspensoes anteriores?\n2. **Politica interna**: Existe regulamento interno ou codigo de conduta assinado?\n3. **Evidencias de desidia**: Quais foram os comportamentos especificos? (atrasos, faltas, entregas atrasadas)\n4. **Tempo de empresa**: Quanto tempo o funcionario trabalhou?\n5. **Salario**: Qual era a remuneracao?\n\nEssas informacoes vao fortalecer a fundamentacao."
  },
  {
    "from": "user",
    "message": "1. Tem 2 advertencias escritas e 1 suspensao de 3 dias. 2. Sim, regulamento interno assinado. 3. Atrasos recorrentes e 3 projetos entregues apos prazo. 4. 2 anos e 4 meses. 5. R$ 18.500."
  },
  {
    "from": "assistant",
    "message": "## Contestacao Trabalhista\n\n**Processo**: [numero]\n**Reclamada**: [nome da empresa]\n**Reclamante**: [nome do ex-funcionario]\n\n### 1. Da tempestividade\nA presente contestacao e tempestiva, apresentada dentro do prazo legal de 15 dias uteis (art. 847, CLT).\n\n### 2. Da justa causa por desidia - Art. 482, \"e\", CLT\n\nA dispensa por justa causa foi aplicada de forma regular e progressiva:\n\n- **1a advertencia escrita** (dd/mm/aaaa): Atraso reiterado no horario de entrada\n- **2a advertencia escrita** (dd/mm/aaaa): Entrega do Projeto X com 15 dias de atraso\n- **Suspensao de 3 dias** (dd/mm/aaaa): Entrega dos Projetos Y e Z fora do prazo acordado\n- **Dispensa por justa causa** (dd/mm/aaaa): Reincidencia no comportamento desidioso\n\nA gradacao das penalidades demonstra que a empresa observou o principio da proporcionalidade...\n\n[Documento completo com 12 paginas gerado]\n\nQuer que eu revise alguma secao ou ajuste a argumentacao?",
    "sources": [
      {"type": "legislacao", "ref": "Art. 482, e, CLT", "verified": true},
      {"type": "legislacao", "ref": "Art. 847, CLT", "verified": true}
    ]
  }
]
```

---

## Documentos / Arquivos

```json
[
  {
    "nome": "Peticao Inicial - Indenizacao.pdf",
    "tipo": "PDF",
    "tamanho": "245 KB",
    "paginas": 8,
    "data_upload": "06/03/2025",
    "status": "Analisado"
  },
  {
    "nome": "Contrato Social - Tech Solutions.pdf",
    "tipo": "PDF",
    "tamanho": "1.2 MB",
    "paginas": 15,
    "data_upload": "05/03/2025",
    "status": "Pendente"
  },
  {
    "nome": "Sentenca - Proc 1098765.docx",
    "tipo": "DOCX",
    "tamanho": "89 KB",
    "paginas": 4,
    "data_upload": "01/03/2025",
    "status": "Analisado"
  },
  {
    "nome": "Comprovante de Residencia.jpg",
    "tipo": "Imagem",
    "tamanho": "3.4 MB",
    "paginas": null,
    "data_upload": "28/02/2025",
    "status": "Pendente"
  },
  {
    "nome": "Procuracao Ad Judicia.pdf",
    "tipo": "PDF",
    "tamanho": "156 KB",
    "paginas": 2,
    "data_upload": "28/02/2025",
    "status": "Analisado"
  }
]
```

---

## Perfis de Advogados

```json
[
  {
    "nome": "Dra. Juliana Lucena",
    "oab": "OAB/SP 198.432",
    "especialidade": "Direito do Trabalho",
    "experiencia": "12 anos",
    "cidade": "Sao Paulo - SP",
    "avaliacao": 4.8,
    "consultas": 340,
    "bio": "Especialista em direito trabalhista com foco em defesa do empregador e compliance corporativo."
  },
  {
    "nome": "Dr. Ricardo Mendes",
    "oab": "OAB/SP 234.567",
    "especialidade": "Direito Civil",
    "experiencia": "8 anos",
    "cidade": "Campinas - SP",
    "avaliacao": 4.6,
    "consultas": 215,
    "bio": "Atuacao em responsabilidade civil, contratos e direito imobiliario."
  },
  {
    "nome": "Dra. Ana Paula Costa",
    "oab": "OAB/RJ 145.678",
    "especialidade": "Direito do Consumidor",
    "experiencia": "15 anos",
    "cidade": "Rio de Janeiro - RJ",
    "avaliacao": 4.9,
    "consultas": 520,
    "bio": "Referencia em direito do consumidor, com historico de atuacao contra grandes empresas."
  },
  {
    "nome": "Dr. Felipe Andrade",
    "oab": "OAB/MG 123.456",
    "especialidade": "Direito de Familia",
    "experiencia": "10 anos",
    "cidade": "Belo Horizonte - MG",
    "avaliacao": 4.7,
    "consultas": 180,
    "bio": "Especialista em divorcio, guarda e inventario. Abordagem humanizada."
  }
]
```

---

## Titulos de Doutrina

```json
[
  {
    "titulo": "Manual de Direito Civil",
    "autor": "Flavio Tartuce",
    "editora": "Metodo",
    "edicao": "14a ed., 2024",
    "paginas": 1280,
    "isbn": "978-85-309-1234-5"
  },
  {
    "titulo": "Curso de Direito Constitucional",
    "autor": "Gilmar Mendes e Paulo Gonet Branco",
    "editora": "Saraiva",
    "edicao": "19a ed., 2024",
    "paginas": 1450,
    "isbn": "978-85-536-2345-6"
  },
  {
    "titulo": "Instituicoes de Direito Processual Civil",
    "autor": "Candido Rangel Dinamarco",
    "editora": "Malheiros",
    "edicao": "10a ed., 2024",
    "paginas": 890,
    "isbn": "978-85-392-3456-7"
  },
  {
    "titulo": "Direito Penal Esquematizado",
    "autor": "Cleber Masson",
    "editora": "Metodo",
    "edicao": "17a ed., 2024",
    "paginas": 1120,
    "isbn": "978-85-309-4567-8"
  },
  {
    "titulo": "Comentarios a CLT",
    "autor": "Homero Batista Mateus da Silva",
    "editora": "Thomson Reuters",
    "edicao": "5a ed., 2024",
    "paginas": 960,
    "isbn": "978-85-203-5678-9"
  }
]
```

---

## Dados Avulsos para Prototipagem

### Tribunais brasileiros (para selects/filtros)
TJ-SP, TJ-RJ, TJ-MG, TJ-RS, TJ-PR, TJ-SC, TJ-BA, TJ-PE, TJ-CE, TJ-GO, TJ-DF, TRF-1, TRF-2, TRF-3, TRF-4, TRF-5, TRF-6, TRT-2, TRT-15, TST, STJ, STF

### Areas do Direito (para filtros/categorias)
Civel, Trabalhista, Criminal, Tributario, Administrativo, Consumidor, Familia, Empresarial, Ambiental, Previdenciario, Eleitoral, Constitucional

### Status de processo (para chips/badges)
Em andamento, Sentenca proferida, Aguardando audiencia, Transitado em julgado, Recurso pendente, Arquivado, Suspenso

### Tipos de documento (para File component)
Peticao Inicial, Contestacao, Sentenca, Acordao, Despacho, Certidao, Procuracao, Mandado, Oficio, Laudo Pericial
