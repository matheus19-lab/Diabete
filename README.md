# Glicose em Foco — PWA inicial

Protótipo local para registrar leituras de glicose do FreeStyle Libre, refeições, aplicações e insulinas cadastradas. Gera um relatório trimestral usando a função de impressão do navegador (selecione “Salvar como PDF”) e monta um prompt detalhado para copiar para uma IA externa.

## Como executar no Ubuntu

1. Extraia o ZIP.
2. Abra um terminal na pasta extraída.
3. Execute:

   ```bash
   python3 -m http.server 8000
   ```

4. Abra `http://localhost:8000` no navegador.
5. Para instalar como PWA, use o menu do navegador e escolha instalar/adicionar à tela inicial, se essa opção estiver disponível.

Não abra apenas `index.html` com `file://`, pois service workers e recursos PWA exigem HTTP/HTTPS.

## O que já funciona

- Cadastro de insulinas personalizadas.
- Registro manual de glicose, tendência do Libre e observações.
- Registro de refeições em texto livre e quantidades.
- Registro de aplicações de insulina.
- Histórico com filtro e exclusão de registros.
- Resumo de leituras e registros.
- Relatório dos últimos três meses: botão “Gerar PDF / Imprimir” abre a impressão do navegador; escolha “Salvar como PDF”.
- Prompt avançado com dados estruturados dos últimos três meses.
- Exportação de backup JSON.
- Lembretes tentativos enquanto o app está aberto; suporte a notificações depende do navegador/permissões.
- Armazenamento local no navegador, sem servidor e sem integração com IA.

## Limitações e segurança

- Os dados ficam no armazenamento local do navegador. Não há criptografia adicional, login, sincronização ou backup automático. Proteja o dispositivo e exporte backups com cuidado.
- A aplicação não lê automaticamente o sensor Libre.
- A aplicação não estima carboidratos automaticamente nem sugere doses.
- O PDF e o prompt distinguem contagens simples de leituras de métricas clínicas completas.
- Não use estimativas geradas por IA para ajustar insulina. Discuta padrões e decisões de tratamento com sua equipe de saúde.
- A PWA é um ponto de partida para desenvolvimento, não um produto médico validado.

## Próximas melhorias sugeridas

1. Banco local IndexedDB com migração e validação mais robustas.
2. Importação autorizada de dados do Libre, se houver método compatível com o modelo/região.
3. Gráficos de evolução e comparações de refeições.
4. Testes automatizados, criptografia local e estratégia de backup.
5. Lembretes mais confiáveis via app móvel/PWA conforme suporte do sistema.



## Onde ficam os dados

No `localStorage` do navegador, por aparelho, navegador e endereço (domínio). Nada é enviado a servidor. Dados em `localhost:8000` não aparecem no endereço publicado. Limpar os dados do site ou desinstalar o navegador apaga tudo: use "Baixar backup JSON" regularmente.
