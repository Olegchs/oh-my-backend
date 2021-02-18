Oh My BackEnd
=============

Документ содержит список базовых навыков, которые **часто** требуются backend разработчику web-приложений. Документ еще находится в процессе доплонения.

Каждый пункт подразумевает что:
- бекендер знает что это и какую проблему решает.
- бекендер знает для чего и когда следует применить.
- бекендер знает как с этим работать или знает где подсмотреть.
- при разработке или проектировании бекендер помнит про них и учитывает в приложении.

Как это работает "внутри" (принцип работы) будет дополнительным бонусом в понимании темы. Если разбираться как работает "внутри" каждый пункт то потребуется очень много времени на изучение, и как следствие, изучайте по желанию и необходимости. Тем не менее это не квантовая физика, глубокое понимание одних технологий упрощает понимание других технологий.

Каждый пункт легко гуглится и имеет страницу в wikipedia. Ссылки устанавливаются если есть альтернативная документация - более понятная и/или подробная.
Ссылка на вики ставятся что бы исключить ошибочного варианта статьи на вики. 
> Цитатой обозначется пояснение к пункту для чего следует это знать и/или где с этим можно столкнуться. Если пояснения нет - то либо не успели сделать, либо там и так ясно `¯\_(ツ)_/¯`.

Каждый пункт делится на градации <kbd>junior</kbd>, <kbd>middle</kbd>, <kbd>middle+</kbd> (он же <kbd>high middle</kbd>).
А где <kbd>sinior</kbd>? Что еще за <kbd>high middle</kbd>? Тут применяется [стандартная градация](https://vas3k.ru/blog/team/) скилов и зон ответвенности.
У всех всё-равно свои разделения на градации, тут они используются что бы помочь разделить кучу тем на то что стоит изучать в первую очередь.
Метка <kbd>guru ⚡</kbd> означает что этот пункт для более глубокого и продвинутого изучения темы (если у Вас есть время).

Если хотите что-то изменить (пункт, ссылку, опечатку) то создавайте [issue](https://github.com/bzick/oh-my-backend/issues) или делайте [pr](https://github.com/bzick/oh-my-backend/pulls). Если хотите обсудить документ то создавайте обсуждение в [discussions](https://github.com/bzick/oh-my-backend/discussions).

В идеале каждый пункт должен иметь градацию, иметь пояснение и иметь ссылку на толковое разъяснение на русском языке. До идеала далеко, но начало положено.

# Содержание

* [Этап 1. Виртуализация docker](#этап-1-виртуализация-docker)
* [Этап 2. Linux](#этап-2-linux)
* [Этап 3. Общие знания](#этап-3-общие-знания)
* [Этап 4. Сеть](#этап-4-сеть)
* [Этап 5. Базы данных](#этап-5-базы-данных)
* [Этап 6. Протокол HTTP](#этап-6-протокол-http)
* [Этап 7. Безопасность](#этап-7-безопасность)
* **[Этап 8. Тут должен быть ваш язык программирования](#этап-8-тут-должен-быть-ваш-язык-программирования)**
* [Этап 9. Электронная почта](#этап-9-электронная-почта)
* [Этап 10. Полнотексовый поиск](#этап-10-полнотексовый-поиск)
* [Этап 11. Метрики](#этап-11-метрики)
* [Этап 12. Проектирование](#этап-12-проектирование)

# Этап 1. Виртуализация docker

Для начала надо поднять виртуальную машину для экспериментов и исследований.
Даже если уже имеете Linux на рабочей машине, всё равно поднимите виртуализацию. В случае чего, виртуальную машину всегда можно пересоздать.
Есть много систем виртуализаций, но docker выделяется среди них. Он один из популярных десктопных виртуализаций и близок с Kubernetes (aka k8s) - популярной серверной виртулизацией.

1. установить [docker](https://www.docker.com/products/docker-desktop) <kbd>junior</kbd>
1. запустить контейнер с Linux Ubuntu, последней [LTS версией](https://ru.wikipedia.org/wiki/Список_версий_Ubuntu#История_выпусков). Запустить bash (консоль) контейнера. <kbd>junior</kbd>
1. установить удобное приложение для урпавления образами и контейнерами [Kitematic](https://kitematic.com/), [Portainer](https://hub.docker.com/r/portainer/portainer/) и тд. Либо сродниться с консольными командами docker. На некоторых OC десктопный docker уже имеет [свой dashboard](https://docs.docker.com/desktop/dashboard/) для управлениея образами и контейнерами. <kbd>junior</kbd>
1. docker compose для поднятия кластера контейнеров. <kbd>middle</kbd>
   > Для рабочего приложения, как правило, требуется несколько различных сервисов (база данных, кешер, http сервер и тд) 
   > и всё это запихать в один docker контейнер будет проблемно, просто из-за специфики работы самого docker-а. 
   > Тут как раз поможет compose что бы запустить кучу контейнеров и подружить их между собой.

# Этап 2. Linux

Изучить установленый в контейнере Linux. Linux де-факто является серверной ос для большинства случаев web-приложений.

1. Установка пакетов и обновление системы через `apt`/`apt-get`/`aptitude`. <kbd>junior</kbd>
   > В процессе исследований и различных проб придётся много раз ставить, обновлять и перставлять множество пакетов linux.
   > Лучше сразу изучить как работают эти команды и чем отличаются.
1. Базовые навыки в `bash` (улучшеный `sh` aka `shell`). <kbd>junior</kbd>
   > В linux-подобных системах башом пронизано всё, вы гарантировано столкнётесь с ним при работе и будут случаи когда надо будет писать bash/shell скрипты.
    * Базовый синтаксис bash. <kbd>middle</kbd>
        * Управляющи операторы `for` и `if`
        * Логические `;`, `&&`, `||`
    * Базовые команды для работы с файловой системой `cd`, `ls`, `find`, `cat`, `cp`, `mv`, `mkdir`, `rmdir`, `rm`. <kbd>junior</kbd>
    * Вызов мануалов через команду `man`. <kbd>junior</kbd>
      > Через эту команду можно получить справку по любой команде, операции, файлам и даже исходному коду.
    * Конвееры команд через оператор `|` (`cmd1 | cmd2 | cmd3`). <kbd>junior</kbd>
      > Linux большое количество команд для обработки данных и для решения различных задач придётся их объединять через коневееры.
    * Команды обработки данных `cat`, `tail`, `head`, `grep`, `awk`, `sed`. <kbd>middle</kbd>
      > Этот набор потребуется для сканирования и анализа логов или больших объёмов текстовых данных.
    * Команды работы с архивами данных `zcat`, `gzip`, `gunzip`, `tar`, `zgrep`. <kbd>middle</kbd>
      > Как правило никто не хранит логи или большие объёмы текстовых данных как есть, обычно это архив `gz` или `tar.gz` (`tgz`).
    * Консольные редакторы `vim`, `nano`. Откыть файл, внести изменения, сохранить. <kbd>junior</kbd>
      > Редактирование файла из консоли не такая редкость. Кстати, что бы выйти из vim: esc, напечатайте `:q!`, enter.
    * Консольные просмоторщики `less`, `zless`. Открыть, найти слово, закрыть. <kbd>junior</kbd>
      > Редакторы избыточны что бы просто посмотреть содержимое файла. Просмоторщик так же справляется с не "стандартными" для редакторов файлами.
    * Фоновые задачи, оператор `&`, команды `jobs`, `fg`, `bg`. <kbd>middle</kbd>
      > Оператор позволит в одной shell сессии запускать несколько команд.
    * Команда игнорирования сигналов прерываний `nohup`. <kbd>middle</kbd>
      > Команда позволит при заверешении shell сессии оставлять в живых запущеннные фоновые задачи до их логического завершения.
    * [Перенаправление потоков](https://www.opennet.ru/docs/RUS/bash_scripting_guide/c11620.html), операторы `>`, `>>`, `<`. <kbd>junior</kbd>
      > Куда писать вывод, а куда ошибки помогут указать эти операции. Для фоновых команд (включая кроны) это обязательные у использованию операторы.
1. Понятие `процесс`. <kbd>junior</kbd>
   > Как и во всех других ОС linux запущенные приложения представляются процессами.
    * Команды анализа процессов `top`, `htop`, `ps` (`ps aux`). <kbd>junior</kbd>
      > Этакий "диспетчер задач" в мире linux, позволяющий мониторить процессы системы.
    * Родительский процесс, дочерний процесс. <kbd>middle</kbd>
      > Процессы не появляются из ниоткуда, их что-то запускает. Понимание иерархии процессов облегчит работу с ними и сделает проще понимание мультипроцессовых приложений.
    * Мастер-воркер процессы, демон (daemon). <kbd>middle</kbd>
      > Это один из распространённых видов распараллеливания вычислений в проиложениях. Много программ используют именно такой подход распараллеливания.
    * Зомби-процессы, откуда берутся, как с ними бороться. <kbd>middle+</kbd>
      > Это вид проблемы распаралелливания вычислений через дочерние процессы. Возникает когда у мастер-процесса есть проблемы или баги.
    * [Отправка сигналов процессам](https://ru.wikipedia.org/wiki/Сигнал_(Unix)). <kbd>junior</kbd>
      > Это основной рычаг воздействия на процессы сторонними приложениями (системными или вашими).
        * Изучение команд `kill`, `pkill`, `killall`. <kbd>junior</kbd>
        * Назначение сигналов [SIGKILL](https://ru.wikipedia.org/wiki/SIGKILL), [SIGTERM](https://ru.wikipedia.org/wiki/SIGTERM), [SIGINT](https://ru.wikipedia.org/wiki/SIGTERM), [SIGHUP](https://ru.wikipedia.org/wiki/SIGHUP), [SIGSEGV](https://ru.wikipedia.org/wiki/SIGSEGV). <kbd>middle</kbd>
    * Системный вызов (syscall). <kbd>middle+</kbd>
      > Системный вызов (вызов API ядра linux) — не бесплатная операция и лучше их держать под контролем на высоконагруженных приложениях.
    * Команада анализа системных вызов процесса через `strace`. <kbd>middle+</kbd>
      > Самый простой и доступный способ посмотреть какие системные вызовы делает процесс в реальном времени.
1. Изучение понятия `дескриптор`. <kbd>middle</kbd>
   > Любой поток данных (входящий и/или исходящий) представляется в виде дескрипторов. Что-либо читать или писать будете (вероятней всего) через дескриптор.
    * Стандартные дескрипторы `STDIN`, `STDOUT`, `STDERR` и их нумерация. <kbd>middle</kbd>
      > Любой поток в процессе пронумерован и есть "зарезервированные" номера под определенные потоки.
    * Потоки, сокеты и unix-сокеты. <kbd>middle</kbd>
      > Это всё разновидности дескрипторов с которыми придётся работать. На всех них распространяются правила дескрипторов, ну так как они и есть дескрипторы.
    * Ограничение на дескрипторы. <kbd>middle+</kbd>
      > Не редкая проблема приложений когда оно упирается в лимит открытых дескрипторов.
    * Команада анализа открытых дескрипторов у процесса через `lsof`. <kbd>middle+</kbd>
      > Для отладки приложения всегда надо знать с чем ведёт общение приложение (отлично работает в паре с `strace`, сопоставляя номера дескрипторов).
1. Права и доступы файловой системы. <kbd>junior</kbd>
    * Супер пользователь, команды `su` и `sudo`. <kbd>junior</kbd>
      > Никто не даст вам root на проде, но вполне можете иметь "привилегированного" пользователя, который умеет в `sudo`.
    * Флаги доступов `x`, `r`, `w` (что они значат для файлов и директорий). <kbd>junior</kbd>
      > Избыточные доступы ведут к дыре в безопасности, недостаток доступов ведёт к багам в приложении. Осмысленно раставляйте где `x` (особенно у директорий), где `r`, а где `w`.
    * Понимание описания доступов вида `--xr-xrwx` и `0137` (восмеричная) у файлов и директорий. <kbd>junior</kbd>
      > Обычно в таком виде вы будете видеть уровни доступов в консолях.
    * Изменение прав доступов через команды `chmod`, `chown`. <kbd>middle</kbd>
1. Ссылки на файловой системе. <kbd>junior</kbd>
    * Symlink (aka символическая ссылка). <kbd>junior</kbd>
      > Самый распространённый вид ссылки. Повсеместно испольузется в linux да и пакетных менеджерах разных языков. Вы тоже будете это использовать.
    * Hardlink (aka жесткая ссылка). <kbd>middle</kbd>
      > Редкий случай использования ссылки. Потребуется если надо "дедуплицировать" большой объем файлов. 
      > По сути позволяет создать несколько имён одному файлу.
1. Исполняемые файлы. <kbd>junior</kbd>
   > Файлы которые могут быть запущены как процессы.
    * [sha bang](https://ru.wikipedia.org/wiki/Шебанг_(Unix)). <kbd>junior</kbd>
      > Ну по сути это костыль что бы сделать скрипты "самозапускаемыми".
1. Запуск и остановка сервисов systemd. <kbd>middle</kbd>
   > Linux по сути просто пачка запущенных приложений как сервисов.
1. [SSH](https://ru.wikipedia.org/wiki/SSH). <kbd>junior</kbd>
   > Самый доступный способ запустить `shell` на удалённой машине это использовать SSH. Используется повсеместно.
    * Генерация собственного ssh-rsa ключа через `ssh-keygen`. <kbd>junior</kbd>
      > Без него вы не попадёте на хосты по SSH.
    * Использование публичного ssh-rsa ключа для входа на удалённую машину (используйте второй контейнер с linux). <kbd>junior</kbd>
1. Перенос контента между хостами. <kbd>junior</kbd>
   > Появляется потребность перекинуть логи, дамп базы и другие файлы между машинами или к себe.
    * `scp`
      > самый простой инструмент переноса файлов между хостами по ssh. <kbd>junior</kbd>
    * `rsync` 
      > пожалуй самый мощный инструмент переноса файлов между хостами с кучами настроек, правил и протоколов. <kbd>middle</kbd>
1. Планировщики задач
   * Работа `crontab`, сапуск `crond`.
     > Самый распрострнённый и просто планировщик задач, с весьма гибкими настройками расписания
   * `at` <kbd>middle</kbd>
     > Когда хотите запустить задачу разово к определенному времени. 
     > В crontab это потребует отдельно создавать расписание, что сильно затруджняет автоматику и захломляет всё расписание.
1. Оперативная память. <kbd>middle</kbd>
    * Команда `free`, мета информация `/proc/meminfo`. <kbd>middle</kbd>
      > Всегда оценивайте сколько памяти потребуется приложению или скриптам, что бы не быть убитыми системой.
    * Ошибка `Out Of Memory` (OOM) и причина появления. [OOM-киллер](https://habr.com/ru/company/southbridge/blog/464245/). <kbd>middle+</kbd>
      > Именно это просиходит когда вы превысили все допустимые пределы потребления памяти в системе.
1. [Логи системы](https://habr.com/ru/post/332502/). Для чего и как посмотреть. <kbd>middle</kbd>
   > Когда случаются проблемы то логи - едиственное что может навести на суть проблемы. Попимо логов приложения стоит заглядывать в логи системы, иногда её проблема может вести к проблеме в приложениях. Стоит выделить некоторые логи:
    * `dmesg` (driver messages) — важные сообщения от компонентов linux, включая от OOM-киллера. <kbd>middle</kbd>
    * `syslog` — системный журнал. <kbd>middle</kbd>
      > Там могут быть сообщения от ядра Linux, различных служб, сетевых интерфейсов и много другого.
1. Проблемы в linux и последствия. <kbd>junior</kbd>
   > Их много, но выделим только несколько.
    * Kernel panic. <kbd>junior</kbd>
      > BSoD аналог для linux. Самая не приятная ошибка системы, явно намекающая что система не стабильна.
    * Segmentation fault (aka segfault aka сегфолт). <kbd>middle</kbd>
      > Не такая редкая ошибка приложений, которые пытаются работать с памятью доступ к которой у них нет.
    * Core dump (aka корка). <kbd>middle+</kbd>
      > Результат обработки segmentation fault системой. Корка может потребоваться разработчку упавшего приложения для анализа состояния программы на момент падения.

# Этап 3. Общие знания

Некоторые знания сложно категоризировать в этом документе. Но без них не обойтись. Это базовые вещи которые используются повсеместно в коде, в системах, "под капотом" вашего языка программирования.

1. Регулярные выражения. Поиграться регулярными выражениями можно [тут](https://regex101.com/). Хоть каждый язык может иметь своё видение регулярных выражений, в общем смысле (и синтаксисе) они похожи. <kbd>middle</kbd>
   > Рано или поздно придётся что-либо спарсить, вот тут как раз и потребуются регулярные выражения.
1. Криптография. <kbd>junior</kbd>
   > Не пугайтесь. Пункт подразумевает прикладное применение криптографических функций (на кой нужны те или иные функции), а не изучении самой криптографии.
    *  Хеши и хеш функции, в том числе `crc32`, `md5`, `sha1`, `sha256`. <kbd>junior</kbd>
    * Цифровые подписи. <kbd>junior</kbd>
      > Что бы обезопасить от подделки данных используются цифровые подписи этих же данных.
    * Cоль для подписей. <kbd>middle</kbd>
      > В теории (да и на практике) хеш функцию можно определить и что бы сильнее обезапасить от "взлома" ваешго хеша, использую так называем ую соль.
    * Коллизии хешей. <kbd>middle</kbd>
      > Хеш функции могут на разные данные вернуть один и тот же результат (хеш), что может привести к проблемам и багам. Лучше знать какова вероятность коллизии у вешей хеш функции и как их избегать.
    * Симметричное и асимметричное шифрование. <kbd>middle+</kbd>
      > Иногда приходится шифровать данные и важно выбрать стретегию шифрования.
    * [Принцип работы TLS](https://habr.com/ru/post/188042/). <kbd>middle+</kbd>
      > Имеется ввиду как работаю CA корневые и промежуточные, что стоит за сертификатом.
1. Базовая работа с `git`. <kbd>junior</kbd> 
   > По факту это дефолтная система контроля версий в мире IT.
    * Комит изменений (commit) <kbd>junior</kbd>
    * Отправка изменений (push/pull) <kbd>junior</kbd>
    * Создание веток и тега (branch/tag) <kbd>junior</kbd>
    * Слияние веток (merge) <kbd>junior</kbd>
    * [упороться полностью git-ом](https://git-scm.com/book/ru/v2)  <kbd>guru ⚡</kbd>
1. Структуры данных. <kbd>junior</kbd> 
    * Хеш таблицы. <kbd>middle</kbd>
      > Таблицы часто испольюзуются в самих языках программирования (ассоциативные массивы, объекты и тд)
    * Очередь и стек. <kbd>junior</kbd> 
      > Самые просты стуктуры данных, которые часто придётся использовать повседневно в коде.
    * [Связный список](https://ru.wikipedia.org/wiki/Связный_список) и [двусвязный список](https://ru.wikipedia.org/wiki/Связный_список#Двусвязный_список_(двунаправленный_связный_список)). <kbd>middle</kbd>
1. Форматы хранения и передачи данных
    * Текстовые. <kbd>junior</kbd>
      > Текстовые форматы используются так же для хранения конфигурации приложений
        * JSON
        * YAML
        * XML
    * Бинарные. <kbd>middle</kbd>
      > Бинарные форматы используются сугубо для хранения и передачи данных.
        * MessagePack
        * BSON (бинарный аналог JSON)
        * ProtoBuf (бинарный аналог XML)

# Этап 4. Сеть

Сеть в разработке самая важная и, часто, мало заметная часть.

1. Базовое понимание работы сети. <kbd>junior</kbd>
   * Протокол TCP <kbd>middle</kbd>
     > Вы вряд ли будете читать пакеты TCP. Но полезно знать КАК работает TCP, 
     > это позволит понять почему при идеальных "интернетах" всё равно приложение может лагать по сети.
     * TCP пакет <kbd>guru ⚡</kbd>
     * Флаги ACK, SYN, FIN и прочие <kbd>middle+</kbd>
     * Буферы (window size) <kbd>middle</kbd>
     * [Проблемы TCP](https://www.youtube.com/watch?v=aXYJlizk3CQ) <kbd>middle+</kbd>
       > TCP очень старый протокол, который не удовлетворяет реалиям. 
       > На видео изобретают свой UDP протокол, рассматривая проблемы TCP и решая их в UDP.
   * Протокол UDP. <kbd>middle</kbd>
     > Самый простой сетевой протокол семейства. Требуется понимание его работы. 
     > HTTP/3.0, DNS работает на протоколе UDP, и понимание UDP даст немного понимания в работе HTTP/3.0
     * UDP пакет <kbd>guru ⚡</kbd>
1. Проблемы сети. <kbd>junior</kbd>
   > Их, как всегда, много. Но стоит выделить те которые явно влияют на скорость работы сети. 
   > По большей части эти проблемы присущи TCP, но могут появиться и там где эмулируют TCP на другом протоколе (например UDP)
   * Packet loss <kbd>junior</kbd>
   * Reordering <kbd>middle</kbd>
   * Jitter <kbd>middle</kbd>
   * Round-Trip Time (RTT aka лаг) <kbd>junior</kbd>
1. IPv4, IPv6.
   > Базовое отличие протоколов надо знать, хотя бы, что б правильно создать колонку IP в базе и обработку в коде.
1. DNS. <kbd>junior</kbd>
   > Ваш код 24/7 будет работать с доменами так как никто не использует чистый IP для соединения куда-либо.
   > Зная как работает DNS и управление резолвингом домена в системе можно упростить отладку в некоторых случаях.
   * [Как работает резолвинг доменов](https://temoto.github.io/a/kak-rabotayut-domeny.html) <kbd>junior</kbd>
   * [DNS записи](https://ru.wikipedia.org/wiki/Типы_ресурсных_записей_DNS) <kbd>middle</kbd>
     * Основные MX, CNAME, NS, A, AAAA, TXT <kbd>middle</kbd>
     * Прочие записи <kbd>middle+</kbd>
   * /etc/hosts <kbd>junior</kbd>
     > Самый просто и доступный способ поменять IP любому домену, локально, конечно же.
   * /etc/resolv.conf <kbd>middle+</kbd>
     > Конфигурация как надо резловить домены и где. 
   * Консольные команды работы с доменами: `whois`, `dig`, `host`. <kbd>junior</kbd>
1. Трассировки маршрутов. <kbd>middle</kbd>
1. Анализ трафика через tcpdump + wireshark <kbd>guru ⚡</kbd>

# Этап 5. Базы данных

Без баз данных - никуда. Самая частый вид баз данных - реляционные. 
Поэтому даже <kbd>junior</kbd> должен уметь работать с реляционными базами данных, 
а вот с noSQL можно знакомится на поздних стадиях.

1. SQL базы данных MySQL/Postgres/итд. <kbd>junior</kbd>
   > MySQL подразумевает как MySQL от Oracle, так и различные модификации как MariaDB, Percona XTraDB. 
   * Базовый синтаксис запросов `SELECT`/`INSERT`/`UPDATE`/`DELETE`. <kbd>junior</kbd>
   * Создание и модификация таблиц <kbd>junior</kbd>
     * Типы колонок таблиц их назначение их различие (на примере MySQL и схожих) <kbd>junior</kbd>
       * tinyint/smallint/int/bigint
       * tinytext/text/mediumtext/longtext
       * set/enum
       * char/varchar
       * decimal
       * double
       * прочие
     * Создание и применение ALTER запросов. <kbd>junior</kbd>
   * Анализ выполнения запросов через `EXPLAIN`, понимание результатов `EXPLAIN`. <kbd>junior</kbd>
     > Самый действенный способ понять почему тормозит запрос. 
   * Ведение логов медленных запросов — slow_log. <kbd>middle</kbd>
     > Не получится сидеть всё время, мониторя все запросы. Проще настроить агрегацию медленных запросов.
   * Индексы <kbd>junior</kbd>
     > Индексы очень важная часть баз данных. Ваши запросы всегда должны работать "по индексам". 
     > Запрос без индекса или с "плохим" индексом, на нагруженных проектах, гарантировано может привести к падению проекта.
     * Назначение PRIMARY индексов <kbd>junior</kbd>
     * Назначение UNIQUE/обычных индексов <kbd>junior</kbd>
     * Составные индексы. <kbd>junior</kbd>
       > Условия и/или сортировки редко когда бывают по одному полю, обычно их больше. Вот тут на сцену выходят составные индексы.
       > Тут надо понимать что в составном индексе последовательность полей важна.
       * Понимание какие поля в какой последовательности добавлять в индекс при фильтрации и/или сортировке. <kbd>middle</kbd>
       * Понимание как строятся деревья индексов у составных индексов. <kbd>middle+</kbd>
     * [Понимание работы индексов](https://ruhighload.com/Индексы+в+mysql) <kbd>middle</kbd>
     * Алгоритм построения индексов `BTREE`. <kbd>guru ⚡</kbd>
       > Это понимание не сделает ваши запросы быстрее, но даст понятие как ведут себя те или иные данные в индексах.
     * Объединение таблиц `LEFT JOIN`, `RIGHT JOIN`, `INNER JOIN`, `OUTER JOIN`, `JOIN`. <kbd>junior</kbd>
       > Данные всегда "размазаны" по таблицам. Что бы их собрать потребуются эти операторы.
     * Группировка данных через `GROUP BY`. <kbd>junior</kbd>
       > Группировка данных — не редкие запросы, как правило, используются для сбора статистики.
       * Фильтрация после группировки. <kbd>junior</kbd>
       * Функции работы с группами MAX/MIN/AVG/итд <kbd>junior</kbd>
     * Понимание и назначение внешних ключей (`foreign key`) <kbd>middle</kbd>
       > Нередко используют внешние ключи для поддержания консистентности данных в базе. 
     * Транзакции. <kbd>middle</kbd>
       > Что бы провести несколько операций атомарно (как одну операцию) используются транзакции.
         * Уровни изоляций транзакций. <kbd>middle</kbd>
         * Deadlock и как его не допускать. <kbd>middle+</kbd>
     * Триггеры на `INSERT`/`UPDATE`/`DELETE`. <kbd>middle</kbd>
       > Не стоит активно использовать триггеры. 
       > Тем не менее они могут оказаться полезными в некоторых отладочных или maintenance случаях.
     * Хранение деревьев. <kbd>junior</kbd>
       > Не просто сохранить древовидную структуру в реляционной базе. Есть насколько анлгоритом со своими плюсами и минусами. 
       > На самом деле актуально и для других видов баз данных
       * parent-child <kbd>junior</kbd>
         > Классический вариант "с parent_id". Простые и "дешевые" на вставку элементов в деревья.
         > Но такие деревья затратные "на сборку".
       * [nested sets](https://devacademy.ru/article/nested-set) <kbd>middle</kbd>
         > Алгоритм позволяет достаточно дёшево собирать деревья с различными модификациями и сегментами.
         > Но затратные на вставку элементов в деревья. 
1. Документо-ориентированная база данных (часть noSQL баз данных) — MongoDB. <kbd>middle</kbd>
   > Как правило, под noSQL подразумевают — MongoDB.  
    * Типы данных в коллекциях их назначение и их различие. <kbd>middle</kbd>
    * Анализ выполнения запросов через `explain()`, понимание его результатов. <kbd>middle</kbd>
    * Понимание работы индексов (аналогично SQL индексам с небольшими отличиями). <kbd>middle</kbd>
      * Sparse свойство индекса
      * Partial свойство индекса
      * TTL свойство индекса
      * Geospatial индекс <kbd>middle</kbd>
      * Text индекс <kbd>middle</kbd>
    * Вложенные объекты, массивы. <kbd>middle</kbd>
    * ⚡ Агрегации <kbd>middle+</kbd>
    * Работа с репликацией. <kbd>middle+</kbd>
    * Работа с кластером MongoDb. <kbd>middle+</kbd>
1. Redis <kbd>junior</kbd>
   > Универсальный инструмент хранения данных с уклоном в производительность. 
   > Может быть, как быстрым постоянным хранилищем, так и реактивным кеширующим временным хранилищем. 
    * [базовая работа с ключами](https://redis.io/commands#generic) <kbd>junior</kbd>
    * [работа со списками](https://redis.io/commands#list) <kbd>junior</kbd>
    * [работа с хешами](https://redis.io/commands#hash) <kbd>junior</kbd>
    * [работа с набором](https://redis.io/commands#set) <kbd>junior</kbd>
    * [сортированным набором](https://redis.io/commands#sorted_set) <kbd>middle</kbd>
    * Работа с Lua. <kbd>middle</kbd>
1. Проблемы в базах данных <kbd>junior</kbd>
    * Deadlock <kbd>middle</kbd>
    * Переполнение числовых полей (в том числе autoincrement) <kbd>junior</kbd>
    * Full scan <kbd>middle</kbd>

# Этап 6. Протокол HTTP

Каждый WEB разработчик должен понимать протокол HTTP. 
Разработчик который не знает HTTP протокол — это как сапожник без сапог. 
Поэтому даже <kbd>junior</kbd> должен знать много про протокол HTTP.

1. [Понимание общего формата протокола](https://developer.mozilla.org/ru/docs/Web/HTTP/Overview): где заголовки, а где тело. <kbd>junior</kbd>
1. Сродниться со вкладкой Сеть/Network в инспекторе браузера <kbd>junior</kbd>
   > В консоли можно наблюдать все HTTP запросы со страницы и даже делать самим через функцию `fetch`.
1. [Методы HTTP запросов.](https://developer.mozilla.org/ru/docs/Web/HTTP/Methods) Их назначение и ограничения. <kbd>junior</kbd>
   * Основные [GET](https://developer.mozilla.org/ru/docs/Web/HTTP/Methods/GET), [POST](https://developer.mozilla.org/ru/docs/Web/HTTP/Methods/POST), [HEAD](https://developer.mozilla.org/ru/docs/Web/HTTP/Methods/HEAD) <kbd>junior</kbd>
   * Прочие `PUT`, `DELETE` итд. <kbd>middle</kbd>
1. [Коды HTTP ответов](https://ru.wikipedia.org/wiki/Список_кодов_состояния_HTTP) <kbd>junior</kbd>
   * Принцип разделения коды на группы 100-199, 200-299, 300-399, 400-499, 500-599. <kbd>junior</kbd>
     > Коды создавались и описывались не в хаотичном порядке. Есть чёткое разделение их "сфер влияния".
     > Даже если какой-то сервер придумает свой код ответа, то по группе сможете лучше понять причину такого ответа. 
   * Основные (частые): 200, 206, 301, 302, 304, 400, 401, 403, 404, 500, 502, 503, 504 <kbd>junior</kbd>
     > Это наиболее частые коды ответов которые гарантировано встретите.
   * [Другие](https://ru.wikipedia.org/wiki/Список_кодов_состояния_HTTP) <kbd>middle</kbd>
1. Заголовки HTTP запроса <kbd>junior</kbd>
   * [MIME тип](https://developer.mozilla.org/ru/docs/Web/HTTP/Basics_of_HTTP/MIME_types) (тип документа) и заголовок типа [Content-Type](https://developer.mozilla.org/ru/docs/Web/HTTP/Заголовки/Content-Type). <kbd>junior</kbd>
     * Формат передачи `application/x-www-form-urlencoded` <kbd>junior</kbd>
     * Формат передачи [multipart/form-data](https://ru.wikipedia.org/wiki/Multipart/form-data) <kbd>middle</kbd>
   * Системные заголовки Host, Content-Length, 
     [Content-Encoding](https://developer.mozilla.org/ru/docs/Web/HTTP/Headers/Content-Encoding), 
     [Transfer-Encoding](https://developer.mozilla.org/ru/docs/Web/HTTP/Headers/Transfer-Encoding)) <kbd>junior</kbd>
   * [Кеширование HTTP](https://developer.mozilla.org/ru/docs/Web/HTTP/Кэширование) и изучение HTTP заголовков управление кешом через `Cache-Control`, `Expires`, `Vary`, `ETag`, `Last-Modified`.
1. [Куки](https://developer.mozilla.org/ru/docs/Web/HTTP/%D0%9A%D1%83%D0%BA%D0%B8) <kbd>junior</kbd>
   > На данный момент это единственный точный способ идентифицировать пользователя.
1. [Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/ru/docs/Web/HTTP/CORS) <kbd>middle</kbd>
   > Для кросс-доменных XHR/WebSocket запросов надо научиться работать с CORS иначе запросы не будут работать.
1. [Content-Security-Policy (CSP)](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy) <kbd>middle</kbd>
   > Для повышения безопасности можно ограничить и указать что и откуда может загружаться и запускаться на странице.
1. Различия версий протокола HTTP/1.0, HTTP/1.1 <kbd>middle</kbd>
   > Не смотря появление новых версий протоколов HTTP версии HTTP/1.0 и HTTP/1.1 всё еще остаются частыми во внутренних сетях кластеров.
1. Консольные команды HTTP запросов `curl`, `wget` <kbd>junior</kbd>
   > На серверах (хостах) нет браузеров, чью удобную консоль можно использовать. 
   > Там есть shell и множество утилит, которые умеют в HTTP.
1. HTTP/2.0 протокол и HTTP/3.0 <kbd>middle+</kbd>
1. WebSocket протокол <kbd>middle</kbd>
   > Это расширения HTTP/1.1 и более до механизма обмена данными по одному соединению. 
   > Часто используется для чатов и/или для event-driven модели.
1. WebRTC <kbd>guru ⚡</kbd>
   > Если надо будет организовывать p2p чаты или p2p стриминг то WebRTC как раз для этого.
1. HTTP API форматы <kbd>junior</kbd>
   * [REST API](https://ru.wikipedia.org/wiki/REST) <kbd>junior</kbd>
   * RPC <kbd>junior</kbd>
   * [GraphQL](https://habr.com/ru/post/326986/) <kbd>middle</kbd>
1. Web сервера <kbd>junior</kbd>
   * [Nginx](https://nginx.org). <kbd>junior</kbd>
     > Самый распространённый Web-сервер. Вероятность натолкнуться на него во время разработки web-приложения - велика.
     * [Ознакомление с базовыми возможностями](https://nginx.org/ru/docs/beginners_guide.html) <kbd>junior</kbd>
     * [Масштабируемая конфигурация nginx](https://www.youtube.com/watch?v=jf3wIN-FwW4) <kbd>middle</kbd>
     * Написание простых локаций в `/etc/nginx/nginx.conf` раздачи файлов <kbd>junior</kbd>
     * HTTP, FastCGI проксирование <kbd>junior</kbd>

# Этап 7. Безопасность

Ваше приложение всегда под угрозой, даже если это какая-то home-page. 
Ботнетам всегда не хватает вычислительных ресурслов. Хакерам - данных. А пользователям - могов (без обид).

1. Виды управления доступом <kbd>junior</kbd>
   * ACL <kbd>junior</kbd>
   * RBAC <kbd>middle</kbd>
1. Аутентификация <kbd>junior</kbd>
   * [Basic](https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication) <kbd>junior</kbd>
     > Самый простой вид авторизации, не требующий дополнительных вычислительных мощностей (серверов).
   * [OAuth2](https://www.digitalocean.com/community/tutorials/oauth-2-ru) <kbd>middle</kbd>
     > Распространенный вид авторизации через посредника, который гарантирует что Вы это Вы и может выдать некоторые данные по пользователю, с его согласия.  
     > Часто сталкиваются c OAuth2 тогда когда надо подключить авторизацию через соц. сети. У них у всех oauth2 (но каждый со своими модификациями).
   * Ldap <kbd>middle</kbd>
     > Данный вид авторизации используется, чаще всего, для авторизации во внутренних сервисах своих сотрудников.
1. Виды атак <kbd>junior</kbd>
   * Фишинг сайта <kbd>junior</kbd>
   * Инъекции (например SQL-иньекции) <kbd>junior</kbd>
   * XSS атака <kbd>junior</kbd>
   * DoS/DDoS <kbd>middle</kbd>
     * HTTP-флуд <kbd>middle</kbd>
     * SYN flood (потребуются знанания TCP) <kbd>middle+</kbd>
     * Медленный запрос <kbd>middle</kbd>
   * Атака посредника (Man In The Middle, MITM) <kbd>middle</kbd>
   * Брутфорс (например бурфорс паролей) <kbd>junior</kbd>
   * Спуфинг <kbd>middle</kbd>
    
# Этап 8. Тут должен быть ваш язык программирования

Языков программирования большое множество. 
Поэтому этот этап будет задевать только часто встречающиеся вопросы в большинстве популярных языков программирования. 
И не будет сильно дробиться на градации, так как это сильно зависит от самого языка. 
Принцип работы с этим разделом: гуглите `%ваш_язык_программирования% %пункт_из_этапа%`. 
Учтите, что **некоторых пунктов может не быть в вашем языке**.

1. Что такое интерпертатор, компилятор, JIT, оп-код, байт-код. Что из этого использует ваш язык? <kbd>junior</kbd>
1. Ваш язык программирования <kbd>junior</kbd>
    * Базовые (примитивные) типы данных в языке.
    * Объекты/классы/прототипы/структуры.
    * Ссылки, слабые ссылки.
    * Garbage Collector.
    * Преобразование типов.
    * Слабая/сильная типизация в коде. На что влияет и как с этим жить.
    * Проблемы в коде
        * Бесконечные циклы
        * Рекурсии
        * Ошибка сегментации (и ее связь с сигналом SIGSEGV)
1. Распараллеливание <kbd>middle</kbd>
    * Различие процессов (созданные через [fork](https://ru.wikipedia.org/wiki/Fork)) от потоков (thread)
        * Поведение дескрипторов до и после fork
    * Потоки (threads)
        * Истинные потоки (pthreads, posix-threads)
        * Зелёные потоки (Green threads)
        * Блокировки Mutex и Семафоры
    * Процессы
        * Разделяемая память (Shared memory)
        * Межпроцессное взаимодействие (IPC)
    * Корутины
    * Проблемы распараллеливания
        * Race Condition
1. Битовые операции: `not`, `and`, `or`, `xor`, сдвиг влево, сдвиг вправо <kbd>junior</kbd>
1. Кеширование данных <kbd>middle</kbd>
    * Частые алгоритмы кеша [LRU](https://ru.wikipedia.org/wiki/Алгоритмы_кэширования#Least_recently_used_(Вытеснение_давно_неиспользуемых)), LFU
    * [Иные алгоритмы кеширования](https://ru.wikipedia.org/wiki/Алгоритмы_кэширования) <kbd>guru ⚡</kbd>
    * Прогревание кеша, инвалидация кеша
1. Сессии (пользователей) <kbd>junior</kbd>
    * Как инициировать
    * Где храняться
    * Параллельное использование одной сессии несколькими запросами
1. Принципы программирования <kbd>junior</kbd>
    * KISS
    * IoC
1. Юнит тестирование <kbd>junior</kbd>
    * Ознакомление с системой тестирования в вашем языке
    * Test-Driven Development (TDD)
1. Специфика работы IO (сокетов, дескрипторов, потоков) <kbd>middle</kbd>
    * Буфферы IO
    * Асинхронный IO
1. Пакетный менеджер или менеджер зависимостей. <kbd>junior</kbd>
1. Работа c HTTP сервером в языке (обработка HTTP запросов). <kbd>junior</kbd>

# Этап 9. Электронная почта

Работа с эл. письмами неотъемлемая часть web разработки (да и не только).
Если не придется создавать письма вручную то читать "сырое" письмо придется.

1. [Спецификация письма MIME](https://www.opennet.ru/docs/RUS/inet_server/servers_glava2_5.html) <kbd>middle</kbd>
   * Основные заголовки: `Return-Path`, `Received`, `From`, `To`, `Cc`, `Bcc`, `Reply-To`, `Subject`, `Message-ID` <kbd>middle</kbd>
   * прочие заголовки <kbd>middle+</kbd>
   * указание кодироквки <kbd>middle</kbd>
   * кодирование полей и тела в base64 <kbd>middle</kbd>
1. Протоколы передачи почты POP3, IMAP <kbd>guru ⚡</kbd>

# Этап 10. Полнотексовый поиск

Каждый разработчик сталкивается с необходимостью полнотекстового поиска, да и вцелом быстрого поиска по куче аттрибутов и текстов.
Для этого используются различные полнотекстовые поисковые движки такие как [ElasticSearch](https://www.elastic.co/), [SphinxSearch](http://sphinxsearch.com/), [ManticoreSearch](https://manticoresearch.com/) и тд.
Самый распространненый полнотексовый поисковый движок с большим комунити — ElasticSearch.

1. Установить Cerebro для работы с ElasticSearch. <kbd>junior</kbd>
1. Индексы <kbd>junior</kbd>
   * Алиасы <kbd>junior</kbd>
   * Настройки <kbd>middle+</kbd>
   * Шаблоны <kbd>middle</kbd>
   * Mapping <kbd>middle</kbd>
1. Запросы <kbd>junior</kbd>
   * Запросы поиска <kbd>junior</kbd>
   * Запросы добавления/обновления/удаления документов <kbd>junior</kbd>
   * bulk запросы <kbd>middle</kbd>
     > Запросы на изменение лучше делать пачкой, так называемым bulk-ом.
   * painless-скриптинг <kbd>middle</kbd>
     > потребуется что бы точечно обновить некоторые поля у документа или вложенные документы, вместо всего документа
1. Подключение морфологий <kbd>junior</kbd>
1. агрегации <kbd>middle</kbd> <kbd>guru ⚡</kbd>
1. работа с nested-документами <kbd>middle</kbd>
1. [ELK](https://www.elastic.co/what-is/elk-stack) <kbd>middle+</kbd>

# Этап 11. Метрики

Любое приложение должно уметь генерировать _полезные_ метрики для системы сбора и анализа метрик. 
По факту сейчас среди opensource акуален [Prometheus](https://prometheus.io/) (или подобные, например, [Victoria Metrics](https://victoriametrics.com/)) для сбора 
и анализа метрик и [Grafana](https://grafana.com/) для их отображения и настройки алертов.

1. Prometheus <kbd>middle</kbd>
   * Типы метрик <kbd>middle</kbd>
     * count
     * gauge
     * histogram
     * summary
   * Варианты отправки метрик: push и pull <kbd>middle</kbd>
   * Запросы (лучше и наглядней делать из Graphana) <kbd>middle</kbd>
     * [Синтаксис](https://prometheus.io/docs/prometheus/latest/querying/basics/) <kbd>middle</kbd>
     * Лейблы
     * Векторы
     * Интервалы
     * Оперторы
   * [Функции](https://prometheus.io/docs/prometheus/latest/querying/functions/), особенно стоит выделить 2 из них: <kbd>middle</kbd>
     * rate
     * irate
1. Graphana <kbd>middle+</kbd>
   * Создание дашбордов
   * Создание графиков
   * Настройка алертов

# Этап 12. Проектирование

Паттерны, концепции и подходы к проектированию различных web-приложений. Пункт в процессе формирования, загляните позже.
