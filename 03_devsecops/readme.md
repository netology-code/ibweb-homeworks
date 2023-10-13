# Домашнее задание к занятию «DevSecOps и AppSec. Часть 2»

Пришлите ответы на вопросы в личном кабинете на сайте [netology.ru](https://netology.ru).

## Описание

Домашнее задание — лабораторная работа, в которой вы по инструкциям выполните действия.

Обратите внимание, что домашнее задание является необязательным. Его выполнение не повлияет на получение зачёта по модулю.

## Задание GitLab

В этом задании применяется сервис GitLab — один из комплексных и самых популярных решений для поддержки DevOps и DevSecOps.

Вы будете использовать пробную версию из облака для упрощения настройки и развёртывания.

Командой GitLab уже подготовлены и настроены инструменты, которые позволяют выполнять действия:
1. Анализировать код на уязвимости — SAST, включая зависимости — SCA или Dependency Scanning.
2. Анализировать контейнеры на уязвимости — Container Scanning.
3. Анализировать используемые в проекте лицензии — License Scanning.
4. Проверять секреты — Secret Detection.

Список всех проверок доступен по адресам:
* https://gitlab.com/gitlab-org/gitlab/-/tree/master/lib/gitlab/ci/templates/Security;
* https://docs.gitlab.com/ee/user/application_security/ (документация).

### Этапы выполнения

1\. Перейдите по [ссылке](https://gitlab.com/-/trial_registrations/new) и зарегистрируйте новую учётную запись. Попросит подтвердить почтовый ящик, поэтому указываем действую почту.

![register01](https://github.com/netology-code/ibweb-homeworks/assets/138114803/dd68e3cb-223c-47c8-9b54-453213c4fcca)


2\. Установите значения, как на скриншоте, и нажмите кнопку **Continue**. (В полях надо указать любую страну и любой номер телефона.)

![trial1](https://github.com/netology-code/ibweb-homeworks/assets/138114803/22b4ef91-564e-409b-a750-e8d024b191c9)

3\. Заполните данные для продолжения.

![welcome_page](https://github.com/netology-code/ibweb-homeworks/assets/138114803/1526e91e-ec88-41d9-96aa-72dc303e1484)

4\. Введите название для группы проектов.

![trial2](https://github.com/netology-code/ibweb-homeworks/assets/138114803/29c4b937-6fa9-45c1-bbca-ac09d5874e09)

5\. Дождитесь перехода на главную страницу.

![start_page](https://github.com/netology-code/ibweb-homeworks/assets/138114803/20c2e05f-321f-4a26-9d95-cf8883477ee4)

6\. Проверьте свой **email**, указанный при регистрации, и подтвердите регистрацию.

![confirm_reg](https://github.com/netology-code/ibweb-homeworks/assets/138114803/c0442513-1ba1-44c7-8efc-1457f81e68bf)

7\. Нажмите на кнопку **Create new project** для создания нового проекта.

![start_page (1)](https://github.com/netology-code/ibweb-homeworks/assets/138114803/f99cc6c8-c6d8-4657-9191-51b46f5b3d1d)

8\. Выберите **Import project** для импорта готового проекта.

![import_project](https://github.com/netology-code/ibweb-homeworks/assets/138114803/2c06ee97-71c9-440d-8c1f-18afa27c18ff)

9\. Нажмите на кнопку **Repository By URL** и заполните поле **Git repository URL** ссылкой: https://github.com/netology-code/ib-devsecops-app.git 

![repo_by_url](https://github.com/netology-code/ibweb-homeworks/assets/138114803/4856f162-dbcf-4237-9ca6-c3514803f1cb)

![repo_by_url_2](https://github.com/netology-code/ibweb-homeworks/assets/138114803/399acb42-657b-4b7a-8e2a-f4c9ba93c1bd)

10\. Оставьте остальные поля заполненными по умолчанию и нажмите **Create project**.

![repo_by_url_2 (1)](https://github.com/netology-code/ibweb-homeworks/assets/138114803/7efdefd7-f740-4c38-9081-7368991cb4ff)

11\. Настройте локальные раннеры

После регистрации, для работы с пайплайнами безопасности, необходимо поставить локальные раннеры на свой компьютер Раннер нужен для сборки и проведения проверок безопасности. Откройте настройки проекта, а именно настройки CI/CD.

![settings_cicd](https://github.com/netology-code/ibweb-homeworks/assets/138114803/344952cd-9fa0-4701-a141-92377816ac58)

Подсказка: адрес имеет вид https://gitlab.com/<название группы>/<название проекта>/-/settings/ci_cd

Внутри настроек переходим к настройкам **Runners**, и нажимем **New project Runner**. Следуем инструкции по настройке раннера **windows/linux/macos** (в зависимости от вашей ОС).

![create_runner](https://github.com/netology-code/ibweb-homeworks/assets/138114803/35531061-3068-44db-bd25-85e8ccf63025)

При успешной настройке, в настройках отобразится локальный раннер.

![runner_good](https://github.com/netology-code/ibweb-homeworks/assets/138114803/17803329-37a2-4a8e-8b60-a1aa4f1737c3)
При этом, необходимо откючить Group runners и Shared runners.

![disable_gr](https://github.com/netology-code/ibweb-homeworks/assets/138114803/ae24be11-53a4-46ed-b93d-9c133ac5fac4)

12\. Перейдите в Settings — CI/CD.

![](12.png)

13\. Найдите пункт Runners и кликните Expand.

14\. Отключите Shared Runners. Не закрывайте эту страницу. Она понадобится нам дальше.

![](14.png)

15\. Сейчас мы создадим gitlab-runner для нашего проекта.

**Установка Runner**

Откройте терминал и введите команду:

```wget https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh```

В примере загружен скрипт для систем на базе пакетов DEB (Ubuntu, Kali).

Открываем его на редактирование:

```nano script.deb.sh```

Находим строки:

```
  # remove whitespace from OS and dist name
  os="${os// /}"
  dist="${dist// /}"
```

И меняем их на что-то подобное:

```
  # remove whitespace from OS and dist name
  os="ubuntu"
  dist="impish"
```

В этом примере описана установка, как для Ubuntu 21.10.

Запускаем скрипт:

```sudo bash script.deb.sh```

После успешной установки введите команду:

```sudo apt-get install gitlab-runner```

После установки gitlab-runner разрешаем автозапуск сервиса и стартуем его:

```sudo systemctl enable gitlab-runner --now```

**Регистрация**

Для корректной работы Runner его нужно связать с нашим проектом в GitLab.

Введите команду:

```sudo gitlab-runner register```

![](15-1.png)

Система в интерактивном режиме запросит данные для регистрации — вводим их:

- **https://gitlab.com/** — адрес нашего сервера GitLab, его можно увидеть на странице с параметрами, которую мы оставили открытой на предыдущем шаге;

- **GR1348941U9SUJxQymbj2KYdVuqxt** — токен для регистрации раннера, его можно увидеть на странице с параметрами, которую мы открывали выше;

- **HomeworkRunner** — произвольное описание для нашего раннера;

- **devsecops, docker, ci/cd** — теги. Рекомендуется максимально точно описывать раннер тегами. С их помощью можно указывать, на каких раннерах должны выполняться те или иные задачи;

- этот пункт опционален, мы его пропускаем;

- **docker** — выбираем исполнителя из предложенных вариантов. В нашем случае это docker;

- **postgres:12.3-alpine** — базовый образ Docker, описан в файле docker-compose.yml.

Конфигурационный файл раннера находится в каталоге /etc/gitlab-runner/config.toml.

Обновим страницу с параметрами для регистрации раннера. Ниже мы должны увидеть, что у нас появился один новый элемент.

![](15-2.png)

Кликните на иконку с изображением карандаша и установите параметры, как на скриншоте ниже.

![](15-3.png)

16\. Теперь раннер создан и зарегистрирован. Если вы ещё раз нажмёте Run pipeline, скорее всего, вы увидите такое состояние. Исправим это.

![](16.png)

17\. Перейдите в /etc/gitlab-runner/.

18\. Отредактируйте config.toml следующим образом:

- найдите строку “privileged = false” и измените “false” на “true”;
- стоку “volumes = ["/cache"]” измените на “volumes = ["/var/run/docker.sock:/var/run/docker.sock", "/cache"]”.

После изменений файл должен выглядеть так:

![](18.png)

19\. Сохраните изменения в файле. После этого процесс анализа должен начаться автоматически.

![](19.png)

20\. Дождитесь окончания процесса анализа.

![](20.png)

21\. Перейдите в раздел Security & Compliance.

![](21.png)

22\. Изучите внимательно разделы:

- Vulnerability Report — отчёт об уязвимостях;
- Dependency List;
- License Compliance.

### Ответьте на вопросы:

**Важно**: после окончания проверки подождите пару минут и несколько раз обновите страницу через `Shift` + `F5`. Иногда не все данные по проверкам подтягиваются сразу. Убедитесь, что уязвимости точно найдены для приложения, зависимостей и контейнера.

**Вопросы для домашнего задания** 

1\. Сколько уязвимостей и какого уровня значимости найдено (Severity)?

![](pic/vulnerabilities.png)

2\. Сколько из них:
- в самом приложении (SAST);
- в контейнерах (Container Scanning);
- в зависимостях (Dependency Scanning);
- секретов (Secret Detection)?

3\. Какая уязвимость найдена в самом приложении?
4\. Сколько зависимостей в приложении?
5\. Сколько различного рода лицензий используется в приложении и его зависимостях?

### Решение задания

Пришлите в личном кабинете ответы на вопросы из раздела «Ответьте на следующие вопросы» и скриншот статистики со всеми найденными уязвимостями. Нужны только числа в секциях `Critical`, `High`, `Medium`, `Low`.

Не удаляйте свою учётную запись после завершения работы. Она вам понадобится на следующей лекции.


