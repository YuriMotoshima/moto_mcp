# Checklist - Deploy

## Antes

- Confirmar repo, branch e commit.
- Confirmar se há mudança de schema/tabela.
- Conferir `.env`/secrets sem expor valores sensíveis.
- Confirmar imagem/compose corretos para o ambiente.
- Confirmar rollback possível.

## Durante

- Baixar o código no servidor.
- Subir containers no projeto correto.
- Evitar comandos destrutivos amplos sem escopo confirmado.
- Conferir health local via `127.0.0.1`.
- Conferir health público via domínio.
- Conferir logs dos serviços principais.

## Depois

- Confirmar status healthy.
- Confirmar DNS/reverse proxy/TLS se houver domínio.
- Confirmar worker/fila/cache/storage/banco se aplicável.
- Registrar pendências reais e não confundir warning histórico com falha nova.
