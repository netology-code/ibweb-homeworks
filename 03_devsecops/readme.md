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


2\. Установите значения, как на скриншоте, и нажмите кнопку `Continue`. (В полях надо указать любую страну и любой номер телефона.)

![trial1](https://github.com/netology-code/ibweb-homeworks/assets/138114803/22b4ef91-564e-409b-a750-e8d024b191c9)

3\. Заполните данные для продолжения.

![welcome_page](https://github.com/netology-code/ibweb-homeworks/assets/138114803/1526e91e-ec88-41d9-96aa-72dc303e1484)

4\. Введите название для группы проектов.

![trial2](https://github.com/netology-code/ibweb-homeworks/assets/138114803/29c4b937-6fa9-45c1-bbca-ac09d5874e09)

5\. Дождитесь перехода на главную страницу.

![start_page](https://github.com/netology-code/ibweb-homeworks/assets/138114803/20c2e05f-321f-4a26-9d95-cf8883477ee4)

6\. Проверьте свой `email`, указанный при регистрации, и подтвердите регистрацию.

![confirm_reg](https://github.com/netology-code/ibweb-homeworks/assets/138114803/c0442513-1ba1-44c7-8efc-1457f81e68bf)

7\. Нажмите на кнопку `Create new project` для создания нового проекта.

![start_page (1)](https://github.com/netology-code/ibweb-homeworks/assets/138114803/f99cc6c8-c6d8-4657-9191-51b46f5b3d1d)

8\. Выберите `Import project` для импорта готового проекта.

![import_project](https://github.com/netology-code/ibweb-homeworks/assets/138114803/2c06ee97-71c9-440d-8c1f-18afa27c18ff)

9\. Нажмите на кнопку `Repository By URL` и заполните поле `Git repository URL` ссылкой: https://github.com/netology-code/ib-devsecops-app.git 

![repo_by_url](https://github.com/netology-code/ibweb-homeworks/assets/138114803/4856f162-dbcf-4237-9ca6-c3514803f1cb)

![repo_by_url_2](https://github.com/netology-code/ibweb-homeworks/assets/138114803/399acb42-657b-4b7a-8e2a-f4c9ba93c1bd)

10\. Оставьте остальные поля заполненными по умолчанию и нажмите `Create project`.

![repo_by_url_2 (1)](https://github.com/netology-code/ibweb-homeworks/assets/138114803/7efdefd7-f740-4c38-9081-7368991cb4ff)

11\. Настройте локальные раннеры

После регистрации, для работы с пайплайнами безопасности, необходимо поставить локальные раннеры на свой компьютер Раннер нужен для сборки и проведения проверок безопасности. Откройте настройки проекта, а именно настройки CI/CD.

![settings_cicd](https://github.com/netology-code/ibweb-homeworks/assets/138114803/344952cd-9fa0-4701-a141-92377816ac58)

**Подсказка:** адрес имеет вид `https://gitlab.com/<название группы>/<название проекта>/-/settings/ci_cd`

Внутри настроек переходим к настройкам `Runners`, и нажимем `New project Runner`. Следуем инструкции по настройке раннера `windows/linux/macos` (в зависимости от вашей ОС).

![create_runner](https://github.com/netology-code/ibweb-homeworks/assets/138114803/35531061-3068-44db-bd25-85e8ccf63025)

При успешной настройке, в настройках отобразится локальный раннер.

![runner_good](https://github.com/netology-code/ibweb-homeworks/assets/138114803/17803329-37a2-4a8e-8b60-a1aa4f1737c3)
При этом, необходимо откючить Group runners и Shared runners.

![disable_gr](https://github.com/netology-code/ibweb-homeworks/assets/138114803/ae24be11-53a4-46ed-b93d-9c133ac5fac4)

12\. Зайдите в пункт меню `Build — Pipelines` и нажмите на кнопку `Run Pipeline`.

![pipeline](https://github.com/netology-code/ibweb-homeworks/assets/138114803/584d0fbe-3da9-4273-b1b4-839ed33ccf76)

13\. На странице снова нажмите на кнопку `Run Pipeline`.

![run_pipeline](https://github.com/netology-code/ibweb-homeworks/assets/138114803/4ce286bc-d467-484f-9fd1-90da17829656)

14\. Дождитесь окончания процесса анализа.

![13_inprogress](https://github.com/netology-code/ibweb-homeworks/assets/138114803/133df17c-a780-431c-98ba-e2e110c0ab0f)

![13_finished](https://github.com/netology-code/ibweb-homeworks/assets/138114803/f83d002d-b6ad-497d-80b5-7e422f9f28b4)

**Примечание.** В списке задач вы увидите упавшую задачу с `retire-js`. Это нормально.

![failed-jobs](https://github.com/netology-code/ibweb-homeworks/assets/138114803/c06b87ae-6938-4b5f-85c1-0e3576b210c0)

![retirejs](https://github.com/netology-code/ibweb-homeworks/assets/138114803/8962d9e9-3379-4678-be4a-57f4a271d3fd)

15\. Перейдите в раздел `Security & Compliance`.

![14](https://github.com/netology-code/ibweb-homeworks/assets/138114803/db101ba4-3f57-4915-83a8-11bdad619f5a)

16\. Изучите внимательно разделы:

- Vulnerability Report — отчёт об уязвимостях;
- Dependency List;
- License Compliance.

### Ответьте на вопросы:

**Важно**: после окончания проверки подождите пару минут и несколько раз обновите страницу через `Shift` + `F5`. Иногда не все данные по проверкам подтягиваются сразу. Убедитесь, что уязвимости точно найдены для приложения, зависимостей и контейнера.

**Вопросы для домашнего задания** 

1\. Сколько уязвимостей и какого уровня значимости найдено (Severity)?

![vulnerabilities](https://github.com/netology-code/ibweb-homeworks/assets/138114803/260031a1-4260-4f56-b743-0ffc5f4cb89e)

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


