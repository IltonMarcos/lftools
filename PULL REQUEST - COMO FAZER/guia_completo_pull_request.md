# Guia Completo: Como Fazer um Pull Request de Forma Segura

Este guia documenta os passos reais realizados para contribuir com o plugin **LFTools** e serve como modelo para futuras contribuições em qualquer ferramenta ou plugin.

---

## 1. O Conceito de Segurança

Para não "quebrar" seu ambiente de trabalho ou o repositório original, usamos o fluxo de **Fork & Branch**:

1. **Fork**: Cria uma cópia do projeto para sua conta no GitHub.
2. **Clone Local**: Baixa o código para uma pasta nova (longe das pastas de sistema).
3. **Branch**: Cria uma ramificação para suas alterações, mantendo a versão original intacta.

---

## 2. Passo a Passo Real (O que fizemos)

Abaixo estão os comandos reais executados no PowerShell para o projeto LFTools.

### Passo A: Criar a pasta de trabalho

```powershell
# Comando Real Usado:
New-Item -ItemType Directory -Force -Path "D:\GEOONE\FORK_LFTools"
```

**O que mudar no futuro?**

- Altere o caminho `"D:\GEOONE\FORK_LFTools"` para o local onde você deseja salvar o novo projeto (ex: `D:\MEUS_PROJETOS\novo_plugin`).

---

### Passo B: Clonar o seu Fork

```powershell
# Comando Real Usado:
git clone https://github.com/IltonMarcos/lftools.git "D:\GEOONE\FORK_LFTools"
```

**O que mudar no futuro?**

- Substitua a URL do GitHub pela URL do seu **novo Fork**.
- Mantenha o novo caminho de destino no final.

---

### Passo C: Criar a Branch de Melhoria

```powershell
# Comando Real Usado:
git checkout -b feature/drone-metadata-improvement
```

**O que mudar no futuro?**

- Altere `feature/drone-metadata-improvement` para um nome que descreva a nova mudança (ex: `fix/erro-de-calculo` ou `feature/nova-ferramenta-xyz`).

---

### Passo D: Copiar o arquivo modificado (A Ponte)

Este passo traz o arquivo que você testou e aprovou no QGIS para a pasta do Git.

```powershell
# Comando Real Usado:
Copy-Item -Path "C:\Users\ilton\AppData\Roaming\QGIS\QGIS4\profiles\default\python\plugins\lftools\processing_provider\Reamb_ImportPhotos.py" -Destination "D:\GEOONE\FORK_LFTools\processing_provider\Reamb_ImportPhotos.py" -Force
```

**O que mudar no futuro?**

- **Path**: Caminho do arquivo original (onde você fez a mudança real).
- **Destination**: Caminho dentro da pasta do Fork que você acabou de clonar.

---

### Passo E: Registrar e Enviar (Commit & Push)

```powershell
# Comandos Reais Usados:
git add processing_provider/Reamb_ImportPhotos.py
git commit -m "Melhoria na extração de metadados de drones DJI e DNG no script Reamb_ImportPhotos.py"
git push origin feature/drone-metadata-improvement
```

**O que mudar no futuro?**

- No `git add`: use o nome do arquivo que você quer subir.
- No `git commit -m`: escreva uma descrição breve da nova mudança.
- No `git push`: use o nome da branch que você criou no Passo C.

---

## 3. Como Finalizar no GitHub

Após o `push`, o terminal mostrará um link.

1. Clique no link ou vá até o seu repositório no site do GitHub.
2. Clique no botão verde **"Compare & pull request"**.
3. Escreva uma descrição profissional (como a que fizemos) e clique em **"Create pull request"**.

---

## Dicas de Ouro (Segurança Extra)

- **Nunca use a senha normal**: Se o Git pedir senha, use o seu **Token de Acesso Pessoal (PAT)**.
- **Git Status**: Use o comando `git status` o tempo todo para ver se está na pasta certa e se o arquivo certo foi modificado.
- **Pasta Isolada**: Mantenha a pasta instalada no QGIS e a pasta do Fork separadas. Só copie o arquivo quando tiver certeza que ele funciona!

PRINT DO QUE FOI FEITO NA REALIDADE:

O Windows PowerShell
Copyright (C) Microsoft Corporation. Todos os direitos reservados.

Instale o PowerShell mais recente para obter novos recursos e aprimoramentos! <https://aka.ms/PSWindows>

PS D:\GEOONE\FORK_LFTools> git clone <https://github.com/IltonMarcos/lftools.git> "D:\GEOONE\FORK_LFTools"
Cloning into 'D:\GEOONE\FORK_LFTools'...
remote: Enumerating objects: 5984, done.
remote: Counting objects: 100% (342/342), done.
remote: Compressing objects: 100% (88/88), done.
remote: Total 5984 (delta 290), reused 291 (delta 254), pack-reused 5642 (from 2)
Receiving objects: 100% (5984/5984), 4.31 MiB | 6.66 MiB/s, done.
Resolving deltas: 100% (4211/4211), done.
PS D:\GEOONE\FORK_LFTools> git checkout -b feature/drone-metadata-improvement
Switched to a new branch 'feature/drone-metadata-improvement'
PS D:\GEOONE\FORK_LFTools> Copy-Item -Path "C:\Users\ilton\AppData\Roaming\QGIS\QGIS4\profiles\default\python\plugins\lftools\processing_provider\Reamb_ImportPhotos.py" -Destination "D:\GEOONE\FORK_LFTools\processing_provider\Reamb_ImportPhotos.py" -Force
PS D:\GEOONE\FORK_LFTools> git status
On branch feature/drone-metadata-improvement
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   processing_provider/Reamb_ImportPhotos.py

no changes added to commit (use "git add" and/or "git commit -a")
PS D:\GEOONE\FORK_LFTools> git add processing_provider/Reamb_ImportPhotos.py
PS D:\GEOONE\FORK_LFTools> git commit -m "Melhoria na extração de metadados de drones DJI e DNG no script Reamb_ImportPhotos.py"
[feature/drone-metadata-improvement ade49cc] Melhoria na extração de metadados de drones DJI e DNG no script Reamb_ImportPhotos.py
 1 file changed, 557 insertions(+), 197 deletions(-)
PS D:\GEOONE\FORK_LFTools> git push origin feature/drone-metadata-improvement
Enumerating objects: 7, done.
Counting objects: 100% (7/7), done.
Delta compression using up to 12 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (4/4), 7.47 KiB | 3.73 MiB/s, done.
Total 4 (delta 3), reused 0 (delta 0), pack-reused 0 (from 0)
remote: Resolving deltas: 100% (3/3), completed with 3 local objects.
remote:
remote: Create a pull request for 'feature/drone-metadata-improvement' on GitHub by visiting:
remote:      <https://github.com/IltonMarcos/lftools/pull/new/feature/drone-metadata-improvement>
remote:
To <https://github.com/IltonMarcos/lftools.git>

- [new branch]      feature/drone-metadata-improvement -> feature/drone-metadata-improvement
PS D:\GEOONE\FORK_LFTools>
