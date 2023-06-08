# **Работа с Git и GitHub**

## 1. Проверка наличия установленного Git 

В терминале выполнить команду  ` git -- version`.
Если Git установлен появится сообщение с информацией о версии программ, иначе будет сообщение об ошибке.

## 2. Установка Git
Загружаем последнюю версию Git с сайта  
https://git-scm.com/downloads.
устанавливаем с настройками по умолчанию.

## 3. Настройка Git
При первом использовании Git необходимо представиться. Для этого необходимо ввести в терминале две команды:
```
git config -- global user.name "Ваше имя"
git config -- global user.email ваша "почта@examle.com"
```
## 4. Инициализация репозитория Git
Инициализацию репозитория неободимо сделать при помощи команды:
`$ git init` 
Неободимо создать папку на диске или на рабочем столе и добавить в репозиторий файл с расширением .tet .md и т.д.

При помощи данной команды происходит инициализация локального репозитория.

## 5. Записи изменений в репозитории Git
Изменения в репозитории выполняются при помощи следующих командах:

 * `$ git status` - получить информацию от git о его текущем состоянии.
 При первои исспользовании терминал выведет на экран 
 On branch master
 No commits yet
 * `$ git add` - добавить файл или файлы к следующему коммиту.
 В терминале будет выглядеть следующим образом:
 `$ git add "Название файла. Расширение"` Расширение указывать обязательно. Чтобы не ошибиться в названии можно ввести первые символы файла и использовать клавишу ТАВ. 
 
 * `$ git commit -m"message"` - создание коммита.
Эта команда всегда идет в совокупности с командой `$ git add`.
Происходит сохранение всех комментариев. Необходимо всегда указывать -а, -m, иначе терминал выдаст ошибку.

 * `$ git diff` - можно увидеть разницу между текущим файлом и закоммиченным файлом. 

 ## 6. Просмотр истории коммитов
 В процессе работы можно посмотреть журнал изменений. Она необходима для отслеживания развития проекта.
Для просмотра истории комитов используется команда:
```
 Git log <название файла>
```
Git log - вывод на экран истории всех коммитов с их хеш-кодами.
У данной команды есть множество вариаций, используя которые можно получить более конкретную и развернутую информацию.

 Так, для промотра истории коммитов со всем ветвями необходимо испорльзовать команду:
 ```
 Git log gruph
 ```
 gruph - представляет дерево взаимосвязей коммитов и позволяет получить графическое представление ветвей прямо в консоли (терминале).
 Для визуализации в этой команде каждая ветвь будет изображена разным цветом.

```
Git -all - на выходе мы получаем итторию всех коммитов существующих веток
```
 ## 7. Перемещение между сохранениями
 Для перемещения на ветку которую мы указали, необходимо выполнить следующий алгоритм:
 Проверить, что указанная нами ветка существует (в инослучае программа не сможет переключиться на ветвь, которая не определена)
 С помощью checkout можно извлечь отдельный файл в ветке в которой мы работаем и перенести его в готовую итоговую ветку (master):

```
 Git checkout <name of new brunch>
```
Для того чтобы вернуться в основную ветку необходимо выполнить команду:

```
 Git checkout master 
```
 ## 8. Игнорирование файлов 

Для того, чтобы исключить из отслеживания в репозитории определенные файлы и папки необходимо создать там файл ***.gitignore*** и записать в него их названия или шаблоны, соответствующие таким файлам или папкам.

## 9. Создание веток в Git
По умолчанию основной веткой в Git - *master*.
Создать ветку можно командой:
```
Git brunch <имя новой ветки>
```
Список веток в репозитории можно посмотреть с помощью команды: 
```
git branch
```
Текущая ветка будет отмечена звездочкой: **\*master**
Для переключения между ветками используется команда: 
```
git checkout <название ветки>
git switch <название ветки>
```
## 10. Слияние веток
Ветвление позволяет разделить рабочий процесс и после того, как написаный кусок готов, его можно отправить к остальной части итоговой версии, удобно переместить его в основную ветку (master).  Для этого в Git предусмотрено слияние - перенос изменений с одной ветки на другую. такие преобразования мы получаем, применив `git merge`:
```
git merge <neme of merged branch>
```
Операция может привести к появлению конфликтов при попытке слить ветки. Это вызвано тем, что изменения удаляют или переписывают информацию в существующих файлах. При попытке некорректного слияния Git останавливает выполнение команды, чтобы вы могли разрешить конфликт.

## 11. Разрешение конфликтов
Конфликт должен выглядить подобным образом: 
<<<<<<<<HEAD
=======
>>>>>>>
При возникновении конфликта между ветками можно "Принять текущее изменение", "Принять входящее изменение", "Принять оба изменения", "Сравнить изменения". Например, мы решили "Принять входящее изменение" тогда из ветки  в данном случае "createBranch" перенесутся все изменения в ветку master. Тогда в тертинале мы увидим соответствующую надпись *(master|MERGING)*. Запись сообщает, что у нас в ветках было слияние с конфликтом.
Далее нужно зафиксировать конфликт (fix conflicts) и выполнить команду ("git commint"). Если мы хотим отменить слияние необходимо: (use "git merge --abort" to abort the merge).
Также стоит упомянуть о существовании ключей, предназначенных специально для работы с конфликтами:

—abort — прерывает слияние и возвращает все к началу
—continue — продолжает слияние после разрешения конфликта
Решить конфликт можно двумя способами:

Вручную разрешить файловый конфликт. Для этого нужно самим изменить файлы, с которыми возникли проблемы. Мы получим файлы такими, какими и представляли их при попытке слияния.
Выбрать более подходящий файл, а от второго отказаться.

## 12. Удаление веток
Для удаления ветки, которую мы слили с веткой master, необходимл в терминале написать коменду: git branch -d (--delete)с указанием ветки которую хотим удалить (к примеру ветку "new"). Увидим сообщение "Deleted branch new (was 5224f7b)".
Если мы не произвели слияние веток, то в терминале будет выведена на экран ошибка: 
*"error: The branch 'createBranch' is not fully merged"*.

Если мы не сделали слияние веток и хотим удалить ветку выполняется команда: git brunch -D <название ветки>. В таком случае происходит принудительное удаление ветки.

Если мы находимся в текущей ветке к примеру "new" и захотим ее удалить, то Git должен вывести сообщение об ошибке: **error: Cannot delete branch 'new' checked out at 'C:/Users/norki/Desktop/GitInstraction'**.

## 13. Работа с изображениями 
Чтобы вставить изображение в текст, достаточно написать следующее:
![atmosfera](1256397.png)

## 14. Работа с GitHub 

1. Зайти на сайт GitHub.com
2. Авторизоваться












