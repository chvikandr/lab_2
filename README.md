# lab_2
## Part I
1. Создайте пустой репозиторий на сервисе github.com.

``$ git init``

``$ git config --global user.name ${GITHUB_USERNAME}``

``$ git config --global user.email ${GITHUB_EMAIL}``

``$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab_2.git``

``$ git push origin master``

2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.

``$ git commit -m""``

``$ git push origin main``

3. Создайте файл hello_world.cpp в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;.

``$ hello_world.cpp <<EOF``

``#include <iostream>``

``using namespace std;``

``int main(){cout << "Hello world" << endl;}``

``EOF``

4. Добавьте этот файл в локальную копию репозитория.

``$ git add hello_world.cpp``

5. Закоммитьте изменения с осмысленным сообщением.

``$ git commit -m"first commit"``

6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.

``$ cat > hello_world.cpp <<EOF``

``#include <iostream>``
  
``#include <string>``
  
``using namespace std;``
  
``int main(){string name; cin >> name; cout << "Hello world" << name << endl; }``
  
``EOF``

7. Закоммитьте новую версию программы. Почему не надо добавлять файл повторно git add?

``$ git commit -a "Change in .cpp"``

8. Запуште изменения в удалёный репозиторий.

``$ git push origin main``

9. Проверьте, что история коммитов доступна в удалёный репозитории.

## Part II
Note: Работать продолжайте с теми же репоззиториями, что и в первой части задания.

1. В локальной копии репозитория создайте локальную ветку patch1.

``$ git branch  patch1``

2. Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std;.

``$ cat > hello_world.cpp <<EOF``

``#include <iostream>``
  
``#include <string>``

``int main()
{
    std::string name;
    std::cin >> name;
    std::cout << "Hello world" << name << std::endl;
}``

``EOF``

3. commit, push локальную ветку в удалённый репозиторий.

``$ git status``

``$ git push origin patch1``

Вывод команды:

Username for 'https://github.com': chvikandr
Password for 'https://chvikandr.com': 
Enumerating objects: 9, done.
Counting objects: 100% (9/9), done.
Delta compression using up to 4 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (5/5), 444 bytes | 444.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0
remote: 
remote: Create a pull request for 'patch1' on GitHub by visiting:
remote:      https://github.com/chvikandr/lab_2/pull/new/patch1
remote: 
To https://github.com/chvikandr/lab_2.git
 [new branch]      patch1 -> patch1
 
 4. Проверьте, что ветка patch1 доступна в удалёный репозитории.

5. Создайте pull-request patch1 -> master.

6. В локальной копии в ветке patch1 добавьте в исходный код комментарии.

``$ cat > hello_world.cpp <<EOF``

``#include <iostream>``

``#include <string>``

``int main()
{
    std::string name; //
    std::cin >> name; // 
    std::cout << "Hello world" << name << std::endl; //
}``

``EOF``

7. commit, push.

``$ git status``

``$ git commit -a "Added comments"``

``$ git push origin patch1``

8. Проверьте, что новые изменения есть в созданном на шаге 5 pull-request

9. В удалённый репозитории выполните слияние PR patch1 -> master и удалите ветку patch1 в удаленном репозитории.

10. Локально выполните pull.

``$ git pull origin main``

Вывод программы

Из https://github.com/chvikandr/lab_2
branch            master     -> FETCH_HEAD
Уже обновлено.

11. С помощью команды git log просмотрите историю в локальной версии ветки master.

``$ git log``

Вывод программы

commit 1dd7c34fc07ccee9be2bf86756e5edce3843bedb (HEAD -> main, origin/main)
Author: chvikandr <g-l-o-120404@rambler.ru>
Date:   Wed May 15 16:20:35 2022 -0500

    ww

commit e29d77dc10c67043bb0c6e28529c5798d3fa3362
Merge: 2132d0d 56c4419
Author: chvikandr <45904292+chvikandr@users.noreply.github.com>
Date:   Wed May 15 16:34:26 2022 +0300

    Merge pull request #1 from chvikandr/patch1
    
    deleting "using namespace std"

commit 56c4419a614a4b90949700d05e4579f0c70e1115
Author: chvikandr <g-l-o-120404@rambler.ru>
Date:   Wed May 15 15:58:27 2022 -0500

    deleting "using namespace std"

commit 2132d0d357165652c9e25a95d0bd1e29e56f7ad4
Author: chvikandr <g-l-o-120404@rambler.ru>
Date:   Wed May 15 15:44:07 2022 -0500

    change in .cpp

commit c0fc06e7d506b1c120a1ef4a8978c46b8281f39c
Author: chvikandr <g-l-o-120404@rambler.ru>
Date:   Wed May 15 15:41:11 2022 -0500

    first commit

(END)

12. Удалите локальную ветку patch1.

``$ git branch -d patch1``

## Part III
Note: Работать продолжайте с теми же репоззиториями, что и в первой части задания. 

1. Создайте новую локальную ветку patch2.

``$ git checkout patch2``

``$ git checkout patch2``

``$ git clone https://github.com/marginoon/timp_lab_2.git -b master``

2. Измените code style с помощью утилиты clang-format. Например, используя опцию -style=Mozilla.

``$ clang-format -style=Mozilla -i ./sources/hello_world.cpp``

3. commit, push, создайте pull-request patch2 -> master.

``$ git status``

``$ git push origin patch2``

4. В ветке master в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.

5. Убедитесь, что в pull-request появились конфликтны.

6. Для этого локально выполните pull + rebase (точную последовательность команд, следует узнать самостоятельно). Исправьте конфликты.

``$ git checkout main``

``$ git pull origin main``

``$ git checkout patch2``

``$ git add hello_world.cpp``

``$ git rebase main``

``$ git rebase --continue``

7. Сделайте force push в ветку patch2

``$ git push -f origin patch2``

Вывод программы:

Username for 'https://github.com': marginoon
Password for 'https://chvikandr@github.com': 
Перечисление объектов: 10, готово.
Подсчет объектов: 100% (10/10), готово.
При сжатии изменений используется до 8 потоков
Сжатие объектов: 100% (9/9), готово.
Запись объектов: 100% (9/9), 1.26 КиБ | 1.26 МиБ/с, готово.
Всего 9 (изменения 2), повторно использовано 0 (изменения 0)
remote: Resolving deltas: 100% (2/2), completed with 1 local object.
To https://github.com/chvikandr/lab_2.git
 + c533e10...a390524 patch2 -> patch2 (forced update)

8. Убедитель, что в pull-request пропали конфликтны.

9. Вмержите pull-request patch2 -> master.
