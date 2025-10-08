export GITHUB_USERNAME=Kinpach
export GITHUB_EMAIL=litclick@yandex.ru
export GITHUB_TOKEN=*** 
alias edit=nano
cd ${GITHUB_USERNAME}/workspace
source scripts/activate
cat > ~/.config/hub <<EOF
github.com:
- user: ${GITHUB_USERNAME}
  oauth_token: ${GITHUB_TOKEN}
  protocol: https
EOF
git config --global hub.protocol https
mkdir projects/lab02 && cd projects/lab02
git init
подсказка: Using 'master' as the name for the initial branch. This default branch name
подсказка: is subject to change. To configure the initial branch name to use in all
подсказка: of your new repositories, which will suppress this warning, call:
подсказка: 
подсказка: 	git config --global init.defaultBranch <name>
подсказка: 
подсказка: Names commonly chosen instead of 'master' are 'main', 'trunk' and
подсказка: 'development'. The just-created branch can be renamed via this command:
подсказка: 
подсказка: 	git branch -m <name>
git config --global user.name ${GITHUB_USERNAME}
git config --global user.email ${GITHUB_EMAIL}
git config -e --global
git remote add origin https://github.com/${GITHUB_USERNAME}/TimpLab02.git
git pull origin master
remote: Enumerating objects: 3, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Распаковка объектов: 100% (3/3), 1.44 КиБ | 1.44 МиБ/с, готово.
Из https://github.com/Kinpach/TimpLab02
 * branch            master     -> FETCH_HEAD
 * [новая ветка]     master     -> origin/master
touch README.md
git status
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	README.md

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
git add README.md
git commit -m"added README.md"
[master 28e8a7a] added README.md
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 README.md
git push origin master
Username for 'https://github.com': Kinpach
Password for 'https://Kinpach@github.com': 
Перечисление объектов: 4, готово.
Подсчет объектов: 100% (4/4), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (2/2), готово.
Запись объектов: 100% (3/3), 277 байтов | 277.00 КиБ/с, готово.
Всего 3 (изменений 0), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: This repository moved. Please use the new location:
remote:   https://github.com/Kinpach/TimpLab02.git
To https://github.com/Kinpach/TimpLab02.git
   e05f658..28e8a7a  master -> master
git pull origin master
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Распаковка объектов: 100% (3/3), 980 байтов | 980.00 КиБ/с, готово.
Из https://github.com/Kinpach/TimpLab02
 * branch            master     -> FETCH_HEAD
   28e8a7a..e05e466  master     -> origin/master
Обновление 28e8a7a..e05e466
Fast-forward
 .gitignore | 4 ++++
 1 file changed, 4 insertions(+)
 create mode 100644 .gitignore
git log
commit e05e46604220eb153522e69cb21ef271771dbb87 (HEAD -> master, origin/master)
Author: Kinpach <litclick@yandex.ru>
Date:   Wed Oct 8 7:15:04 2025 +0300

    Create .gitignore

commit 28e8a7ae652e231dd4467ae646edc79c2be7d4b4
Author: Kinpach <litclick@yandex.ru>
Date:   Wed Oct 8 7:15:57 2025 +0300

    added README.md

commit e05f65811fe99c3cfec00c8e6a1267650c8ed3fa
Author: Kinpach <litclick@yandex.ru>
Date:   Wed Oct 8 7:16:29 2025 +0300

    Initial commit
mkdir sources
mkdir include
mkdir examples
cat > sources/print.cpp <<EOF
#include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
EOF
cat > include/print.hpp <<EOF
#include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
EOF
cat > examples/example1.cpp <<EOF
#include <print.hpp>

int main(int argc, char** argv)
{
  print("Hello world!");
}
EOF
cat > examples/example2.cpp <<EOF
#include <print.hpp>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("Hello world!"), file);
}
EOF
edit README.md
git status
Текущая ветка: master
Неотслеживаемые файлы:
  (используйте «git add <файл>...», чтобы добавить в то, что будет включено в коммит)
	examples/
	include/
	sources/

индекс пуст, но есть неотслеживаемые файлы
(используйте «git add», чтобы проиндексировать их)
git add .
git commit -m"added sources"
[master eaf240d] added sources
 4 files changed, 32 insertions(+)
 create mode 100644 examples/example_1.cpp
 create mode 100644 examples/example_2.cpp
 create mode 100644 include/print.hpp
 create mode 100644 sources/print.cpp
git push origin master
Username for 'https://github.com': Kinpach
Password for 'https://Kinpach@github.com': 
Перечисление объектов: 10, готово.
Подсчет объектов: 100% (10/10), готово.
При сжатии изменений используется до 3 потоков
Сжатие объектов: 100% (7/7), готово.
Запись объектов: 100% (9/9), 959 байтов | 959.00 КиБ/с, готово.
Всего 9 (изменений 0), повторно использовано 0 (изменений 0), повторно использовано пакетов 0
remote: This repository moved. Please use the new location:
remote:   https://github.com/Kinpach/TimpLab02.git
To https://github.com/Kinpach/TimpLab02.git
   e05e466..eaf240d  master -> master
