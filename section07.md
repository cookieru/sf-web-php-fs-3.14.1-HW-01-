[<< Вернуться к оглалению](README.md) | [< Предыдущий раздел](section06.md) | [Следующий раздел >](section08.md)

Отмена индексации, отмена изменений
===================================

>В Git существуют несколько способов отмены сделанных изменений. Однако, не все операции отмены могут быть сами по себе отменены, поэтому нужно быть осторожным. Git - одна из немногих областей, где неправильные действия могут привести к __необратимым результатам__.

Параметр --amend команды git commit. Перезапись прошлого коммита
----------------------------------------------------------------

Отмена может потребоваться, если вы сделали коммит слишком рано, без некоторых файлов или комментария к коммиту. Если вы хотите переделать коммит, вам нужно внести необходимые изменения, добавить их в индекс и сделать коммит повторно, используя опцию __--amend__.

Параметр __--amend__ позволяет вносить изменения в уже существующий коммит с помощью индекса. Если вы с момента последнего коммита ничего не изменили, то состояние останется таким же, а изменить можно только сообщение коммита. Вы можете редактировать это сообщение как обычно, и оно заменит сообщение предыдущего коммита.

Например, если вы сделали коммит и поняли, что забыли добавить изменения файла, который хотели включить в коммит, вы можете выполнить следующие действия:

```
git commit -m 'Initial commit'
git add forgotten_file
git commit --amend
```

Этим действием будет создан единый коммит, в котором второй коммит заменит результаты первого.

>Важно понимать, что при внесении изменений в последний коммит вы фактически заменяете его новым коммитом, который полностью перезаписывает предыдущий. Как результат, кажется, что первоначальный коммит никогда не существовал и больше не будет виден в истории вашего репозитория. Очевидно, цель изменения коммитов состоит в добавлении незначительных изменений в последние коммиты и избегании засорения истории сообщениями вроде "Ой, забыл добавить файл" или "Исправление грамматической ошибки".

Команда git restore.
------------------------------------

Иногда бывает необходимость убраььт файл из индекса перед коммитом, например, если файл был добавлен случайно. В выводе команды `git status` есть подсказка как отменить индексацию:

![отмена индексации в git status]()

После ее выполнение файл больше не находится в состоянии _staged_

![результат отмены индексации в git status]()

А иногда бывает ситуации, когда файл необходимо вернуть в состояние, в котором он был на момень последнего коммита. Опять же, в выводе команды `git status` есть информация как сделать и это:

![отмена изменений в git status]()

После ее выполнение файл больше не находится в состоянии _modified_

![результат отмены изменений в git status]()

>Команда `git restore` - это действительно мощный инструмент в Git, но он может быть опасным, если не использовать его правильно. Эта команда позволяет отменить изменения в указанном файле и вернуть его к последней сохраненной версии в репозитории. Поэтому следует быть внимательным и сохранять резервные копии файлов в безопасном месте перед использованием этой команды, если есть любые сомнения.

Если вы делали изменения в файле и хотите сохранить их, но в данный момент нужно отменить эти изменения, то в Git есть несколько способов, которые могут быть более эффективными. Один из таких способов - ветвление, которые мы подробнее рассмотрим в [Ветвление в Git](section09.md).

[<< Вернуться к оглалению](README.md) | [< Предыдущий раздел](section06.md) | [Следующий раздел >](section08.md)