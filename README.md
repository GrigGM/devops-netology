# Домашнее задание к занятию "Системы контроля версий" - Григорьев Геннадий
---

### Задание 1

Создал публичный репозиторий на https://gitflic.ru/ (консольная утилита установлена и настроена). Клонировал репозиторий, используя протокол HTTPS
```
git clone https://gitflic.ru/project/gmgrig/devops-netology.git
```
В директории с клонированным репозиторием произвел первоначальную настройку и создал файл README.md (в отличии от github нет опции по его автоматическому созданию)

```
git config --global user.name "Grigoryev Gennady"
git config --global user.email "gmgrig@gmail.com"

git add README.md
git commit -m "add README"
[master (root-commit) e727dfb] add README
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
git push -u origin master
Enumerating objects: 3, done.
Counting objects: 100% (3/3), done.
Writing objects: 100% (3/3), 220 bytes | 220.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote: Updating references: 100% (1/1)
To https://gitflic.ru/project/gmgrig/devops-netology.git
 * [new branch]      master -> master
branch 'master' set up to track 'origin/master'.
```

```
> git status
On branch master
Your branch is up to date with 'origin/master'.

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
> git diff
diff --git a/README.md b/README.md
index e69de29..4309518 100644
--- a/README.md
+++ b/README.md
@@ -0,0 +1 @@
+# Домашнее задание к занятию "Системы контроля версий" - Григорьев Геннадий
> git diff --staged
>
```
После перевода файла в состояние staged
```
> git add README.md
> git diff
> git diff --staged
diff --git a/README.md b/README.md
index e69de29..35410bd 100644
--- a/README.md
+++ b/README.md
@@ -0,0 +1,33 @@
+# Домашнее задание к занятию "Системы контроля версий" - Григорьев Геннадий^M
+^M
```
и после коммит
```
> git diff
> git diff --staged
> git status
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean
>
```
Добавил файл .gitigore

```
git status
```
![Скриншот 1](./img/img1.png)

Создал директорию terraform, а внутрь поместил [.gitigore](https://github.com/github/gitignore/blob/main/Terraform.gitignore) из шаблона (будет действовать внутри директории). В нем следующие исключения:
- `**/.terraform/*` Скрытая директория, которую Terraform использует для управления кэшированием, записывает, какая рабочая область активна в данный момент, и записывает последнюю известную конфигурацию серверной части на случай, если потребуется перенести состояние при следующем запуске. Этот каталог автоматически управляется Terraform и создается во время инициализации.
- `crash.log` и `crash.*.log` Файлы журналов сбоев.
- `*.tfvars` и `*.tfvars.json` Исключает все файлы .tfvars, которые могут содержать конфиденциальные данные, например пароль, секретные ключи и другие секреты. Они не должны быть частью версии контроль, поскольку они представляют собой точки данных, которые потенциально конфиденциальны и подвержены меняться в зависимости от окружающей среды.

и т.д.

Закоммитил все новые и изменённые файлы.

Для удаления файла с диска и из репозитория воспользуюсь командой
```
git rm .\will_be_deleted.txt
```
Для перемещения воспользуюсь командой 
```
git mv .\will_be_moved.txt has_been_moved.txt
```
![Скриншот 2](./img/img2.png)

Итоговый вывод `git log`

![Скриншот 3](./img/img3.png)

## Работа над ошибками

Восстановил доступ к https://github.com/ и выпустил персональный токен

```
 winget install --id GitHub.cli

 git remote -v
origin  https://gitflic.ru/project/gmgrig/devops-netology.git (fetch)
origin  https://gitflic.ru/project/gmgrig/devops-netology.git (push)

git remote add github https://github.com/GrigGM/devops-netology.git

git remote -v
github  https://github.com/GrigGM/devops-netology.git (fetch)
github  https://github.com/GrigGM/devops-netology.git (push)
origin  https://gitflic.ru/project/gmgrig/devops-netology.git (fetch)
origin  https://gitflic.ru/project/gmgrig/devops-netology.git (push)

git push -u github master

Необработанное исключение: System.ComponentModel.Win32Exception: Недопустимый дескриптор окна
   в MS.Win32.ManagedWndProcTracker.HookUpDefWindowProc(IntPtr hwnd)
   в MS.Win32.ManagedWndProcTracker.OnAppDomainProcessExit()
   в MS.Internal.ShutDownListener.HandleShutDown(Object sender, EventArgs e)
Enumerating objects: 28, done.
Counting objects: 100% (28/28), done.
Delta compression using up to 8 threads
Compressing objects: 100% (21/21), done.
Writing objects: 100% (28/28), 97.79 KiB | 12.22 MiB/s, done.
Total 28 (delta 6), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (6/6), done.
To https://github.com/GrigGM/devops-netology.git
 * [new branch]      master -> master
branch 'master' set up to track 'github/master'.
```