# Entrega e regras de negócio

Construí a central para que a área solicitante acompanhasse suas demandas no POP e a equipe técnica mantivesse a execução no Azure DevOps. O resumo de entrega registra conclusão do escopo e reunião de validação e repasse como próximo passo.

## Abertura e acesso

A rota documentada é `/tickets`. Acesso, leitura e edição dependem de equipe e perfil, incluindo Tecnologia, Produto, BI e administração. O fluxo `NewTicketFlow` segue setor → tipo → área → detalhes.

| Tipo | Uso documentado |
| --- | --- |
| RTN | Rotinas e demandas recorrentes |
| BUG | Erros e falhas de funcionamento |
| QST | Solicitação de desenvolvimento/questionamento, exclusiva da fila de Produto |

As áreas são ordenadas alfabeticamente, com Outros no final. Rotinas padronizadas oferecem download de modelo e exigem anexo. Cliente, conta, identificadores, prioridade, descrição e detalhes compõem o contexto da solicitação.

## Validação e responsáveis

A validação utiliza `validated_at` e `validated_by`, separados do status operacional. O botão Validado e a movimentação manual correspondente devem produzir o mesmo efeito: criar o item no Azure uma única vez. Atualizações posteriores do webhook preservam essa aprovação. A sequência documentada após validação inclui Em progresso e Concluído.

Em BUG, o responsável é escolhido em lista fechada do time de Tecnologia no POP, incluindo Sem responsável, sem ser enviado ao Azure. Em RTN e demais tipos, vem do Azure e é somente leitura no POP. Para o solicitante, atualizações originadas no Azure aparecem como Time de Tecnologia.

## Comunicação e acompanhamento

Lista e Kanban oferecem filtros, busca e avisos de nova mensagem. O detalhe reúne cliente, conta, IDs e acesso ao número Azure, descrição recolhível e abas Anexos, Conversa e Últimas Atualizações. Preferências de recolhimento são individuais.

A conversa usa referências visuais de Teams/WhatsApp: agrupamento por autor em janela de cinco minutos, mensagens próprias à direita, separadores de data, texto rico e imagens. Enter envia e Shift+Enter insere quebra de linha. A interface usa atualização otimista e a conversa continua disponível após validação. Esse padrão visual não significa integração com APIs de Teams ou WhatsApp.

A opção Notificar solicitante gera um sino de alerta no Kanban/lista; abrir o card limpa o alerta. Anexos usam URLs assinadas, com regras de acesso e remoção por autor, produto e etapa.

O histórico reúne status, responsáveis, comentários e interações relevantes, com resumos executivos de IA. O documento cita atualização em tempo real de `ticket_assignment_history` e nova consulta ao abrir o ticket ou retornar o foco.
