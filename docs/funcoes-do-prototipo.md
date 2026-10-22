# Funções recuperadas do HTML

Estas funções existem em `prototype/index.html`. São funções de interface e manipulação de dados demonstrativos em memória.

| Função | Responsabilidade |
| --- | --- |
| `getStatusBadge` | Formata indicador visual do status |
| `getSectorBadge` | Formata o setor |
| `getPriorityDot` | Define cor e rótulo da prioridade |
| `getTypeBadge` | Identifica RTN, BUG e QST |
| `openDetail` / `closeDetail` | Abrem e fecham detalhes do ticket |
| `renderList` / `renderKanban` | Montam as visões gerais a partir de `ticketsData` |
| `renderTechList` / `renderTechKanban` | Montam as visões da fila técnica |
| `cycleValidationState` | Alterna a validação visual e atualiza o registro em memória |
| `updateValidationButtonUI` | Atualiza texto, ícone e aparência da validação |
| `goToStep` / `backToSector` / `closeFlow` | Controlam etapas e fechamento do formulário |
| `init` | Inicializa comportamento e renderização |

Entrada → objetos JavaScript demonstrativos e ações de interface. Processamento → renderização e mudanças locais. Saída → tabelas, cards e painel de detalhes.

`cycleValidationState` pertence à versão histórica da tela. Ela não implementa a persistência independente de `validated_at`/`validated_by` descrita na entrega posterior. Recarregar a página desfaz as mudanças locais. Não há criação real de item Azure nem persistência no banco.
