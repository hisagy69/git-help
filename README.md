# FirstProject

Шпаргалка по командам Git

---

```bash
git init
```
нужен для того, чтобы создать локальный репозиторий

```bash
git add
```
нужен для того, чтобы добавить файл в индекс
если указать имя файла, то будет добавлен только этот файл, если указать ".", то будет добавлен весь репозиторий 

```bash
git status
```
покажет какие изменения были подготовлены, а какие нет и какие файлы отслеживаются git
в Git существуют различные статусы файлов описывающих их состояние:
1. Неотслеживаемый (untracked) - это файл, который был добавлен в рабочую директорию, но еще не был добавлен в индекс.
2. Измененный (modified) - это файл, который был изменен в рабочей директории, но еще не был добавлен в индекс.
3. Отслеживаемый (tracked) - это файл, который был добавлен в рабочую директорию, и был добавлен в индекс.
4. Подготовленный (staged) - это файл, который был добавлен в индекс и готов к комиту.
5. Игнорирумый (ignored) - это файл, который включен в файл .gitignore и не отслеживается git.

```bash
git commit -m
```
сохранить изменения в локальном репозитории
флаг -m передает описание

```bash
git log
```
покажет всю историю коммитов
HEAD - текущий коммит
флаг --oneline выведет каждый коммит в одну строку сокращая хэш до необходимого мимнимума, чтобы тот был уникальным в рамках репозитория

```bash
git remote add origin [url репозитория, например git@github.com:hisagy69/test.git]
```
подключить локальный репозиторий к удаленному репозиторию
origin - имя репозитория

```bash
git remote -v
```
покажет с каким удаленным репозиторием связан

```bash
git clone [ссылка на репозиторий]
```
загрузит удаленный репозиторий и свяжет локальный репозиторий с удаленным

```bash
git push -u origin master
```
отправить изменения в удаленный репозиторий
флаг -u свяжет локальную ветку с одноименной удаленной
master - ветка
чтобы запушить любую ветку, можно указать git push -u origin <имя ветки>

```bash
git diff
```
показывает изменения относительно последнего коммита для неиндексированных файлов
@@ -1,10 +1,10 @@ - выводит номер строки в которой произошли изменения (в данном примере изменения на первой строчке и занимают 10 строк).
если добавить флаг --staged, то выведет изменения проиндексированных файлов относительно последнего коммита
указав после git diff хеш для двух коммитов, увидим изменения, которые произошли между этими коммитами
сравнивать также можно название веток или название ветки и коммит

---
## Как откатиться

```bash
git commit --amend
```
позволяет в комите добавить новые файлы или добавить изменения в файлах
если указать флаг -m, то можно заменить текст комментария
если указать флаг --no-edit, то можно заменить коммит новой версией, не меняя сообщение

```bash
git restore --staged <file>
```
позволяет удалить файл из индекса
если указать за место файла точку ".", то тогда индекс удалится от всех файлов

```bash
git reset --hard <commit hash>
```
позволяет откатиться к определенному коммиту, предыдущие коммиты при том удаляются

```bash
git reset <file>
```
позволяет откатить изменения, которые не попали ни в staged, ни в коммит

---
## Ветки

```bash
git branch
```
посмотреть список веток
*отмечена ветка в которой находишься
если указать флаг -D или -d, то произойдет удаление ветки (надо находиться в другой ветке)

```bash
git branch <название ветки>
```
создаст новую ветку

```bash
git checkout <имя ветки>
```
сменить ветку
если указать флаг -b, то ветка будет создана и мы сразу в нее переместимся

```bash
git merge <имя ветки>
```
выполнить слияние ветки
при выполнении слияния, нужно находиться в ветке, в которую происходит слияние
