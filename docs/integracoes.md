# APIs e integrações

## O que foi recuperado

| Integração | Papel na entrega | Evidência disponível |
| --- | --- | --- |
| Azure DevOps | Criar item após validação e sincronizar status, prioridade, severidade, responsáveis, comentários e anexos | Resumo de entrega e histórico de configuração |
| Webhook Azure → POP | Receber alterações e manter o histórico | Resumo de entrega; histórico menciona `workitem.updated`, `workitem.commented` e `workitem.deleted` |
| Gemini Flash | Traduzir atualização técnica em resumo para CS/solicitante | Resumo de entrega |
| E-mail | Comunicar criação do ticket | Resumo de entrega |
| Portal ISO | Abertura automática no fluxo de novo cliente | Resumo de entrega |
| Vendas/Pipedrive | Apoiar identificação do solicitante | Cascata documentada: Vendas/Pipedrive → usuário POP → fallback |

O histórico recuperado também menciona uma Edge Function Supabase chamada `azure-devops-webhook`. Esse registro é contexto de implementação, não o código da função ou confirmação de sua versão final. Não recuperamos rotas completas, contratos HTTP, consultas SQL, políticas de acesso ou configuração de autenticação. Não reconstruí esses elementos por suposição.

## Regras de sincronização descritas

1. Validar o ticket e registrar a aprovação independentemente do status.
2. Criar o item no Azure uma única vez.
3. Receber alterações técnicas, mantendo prioridade e severidade como campos distintos.
4. Deduplicar atualizações por hash e evitar eventos falsos de troca de responsável.
5. Preservar a validação ao atualizar o estado operacional.
6. Apresentar o histórico e, quando aplicável, um resumo acessível ao solicitante.

O formato do hash e o mecanismo transacional de criação única não constam nos arquivos recuperados. As regras de responsável variam por tipo e estão detalhadas em [entrega-e-regras.md](entrega-e-regras.md).

## IA e continuidade

O uso documentado de Gemini Flash transforma comentários técnicos em comunicação compreensível. Quando não há comentário técnico, existe uma mensagem de continuidade como fallback. O prompt exato e o código de chamada não foram recuperados. O exemplo neste repositório é ilustrativo, não uma saída de produção.

## Limite de execução

Os HTMLs usam dados locais. Não contêm chamadas REST de integração com Azure ou Gemini. Este repositório permite estudar interface, regras e arquitetura, mas não oferece um backend pronto para implantação. A validação ponta a ponta depende do ambiente original, ao qual não tenho mais acesso.
