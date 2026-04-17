---
name: github-pr-master
description: Guia de orientação para contribuições via Pull Request no GitHub (CLI e GUI)
---

# GitHub PR Master Skill

Esta habilidade orienta como guiar o usuário em um processo de contribuição de código para repositórios GitHub, mantendo a integridade do ambiente local e garantindo uma representação profissional perante os proprietários dos repositórios.

## Princípios de Orientação
1. **Segurança em Primeiro Lugar**: Sempre utilize o fluxo de Fork. Nunca oriente o usuário a modificar diretamente a pasta de perfil/sistema sem uma cópia isolada.
2. **Dualidade de Interface**: Para cada passo, ofereça a opção de comando (CLI) ou guia visual (GUI).
3. **Didática de Adaptação**: Ao fornecer um comando, explique claramente quais partes são específicas do projeto atual e o que deve ser mantido.

## Fluxo de Trabalho (Workflow)

### 1. Preparação (Fork)
- **GUI**: Instruir o usuário a clicar no botão "Fork" no repositório original.
- ** CLI**: Se o usuário tiver o `gh cli`, usar `gh repo fork <url>`.

### 2. Sincronização Local (Clone)
- **Local**: Sugerir sempre uma pasta fora do `AppData` ou pastas de programa.
- **Passo**: `git clone <url-do-fork> <diretorio-alvo>`.

### 3. Isolamento de Alteração (Branching)
- **Regra**: Nunca trabalhar na `main`. 
- **Padrão**: Criar branches com prefixos `feature/` ou `fix/`.

### 4. Integração de Alterações
- Orientar o usuário a copiar o arquivo modificado (que foi testado no QGIS/App) para o diretório do Fork.
- Usar `Copy-Item` (PowerShell) ou Arrastar/Soltar (Windows Explorer).

### 5. Ciclo de Envio (Commit & Push)
- **Verificação**: Sempre pedir ao usuário para rodar `git status` antes de prosseguir.
- **Commit**: Sugerir mensagens claras em Português ou Inglês (conforme o projeto).
- **Push**: `git push origin <nome-da-branch>`.

### 6. Submissão do PR
- Capturar o link gerado no terminal após o push e fornecer ao usuário.
- **Template de Descrição**: Fornecer um modelo de texto para o campo de descrição do PR, destacando:
    - O que foi mudado.
    - Por que é importante.
    - Como testar.

## Comandos Recomendados

### PowerShell / Git CLI
```powershell
# Sincronizar
git clone <url>
git remote add upstream <url-original>

# Trabalho
git checkout -b <branch-name>
Copy-Item -Path <origem> -Destination <destino> -Force

# Envio
git add .
git commit -m "Mensagem clara"
git push origin <branch-name>
```

## Guia Visual (GUI)
- No site do GitHub: Abas "Code", "Pull Requests", botão "Compare & pull request".
- No Windows: Uso de terminais como o Prompt de Comando ou PowerShell dentro das pastas específicas.
