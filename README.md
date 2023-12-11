# Домашнее задание к занятию "Системы контроля версий" - Григорьев Геннадий

---

### Задание 1

Создал публичный репозиторий на https://gitflic.ru/ (консольная утилита установлена и настроена). Склонировал репозиторий, используя протокол HTTPS

```
git clone https://gitflic.ru/project/gmgrig/devops-netology.git
```
В директории с клонированным репозиторием произвел первоначальную настройку и создал файл README.md

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

