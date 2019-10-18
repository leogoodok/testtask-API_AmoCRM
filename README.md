# testtask.wotskill.ru. Взаимодействие сайта с аккаунтом AmoCRM.ru через API.

Особености. Задание должно выполняться на:
- PHP без использования Фреймовков;
- JS (JQuery).


# Краткое описание задания.

* Создать пробный аккаунт [AmoCrm](https://www.amocrm.ru/)
* Создать JS скрипты: Обработки и отправки заявки с сайта.
* Создать PHP скрипты:
  - Авторизации в аккаунте AmoCrm через средства API;
  - Добавление контакта в AmoCrm через API;
  - Добавление сделки AmoCrm через API;
  - Добавление задачи AmoCrm через API;
  - Добавление примечания AmoCrm через API.


## Задание 1 (Дополнительное).

1. Написать простейшую форму со следующими полями.
- Фамилия;
- Дата рождения;
- Номер телефона;
- Адрес электронной почты;
- Марка авто.

2. Настроить валидацию формы (на стороне пользователя).

- Фамилия (обязательное поле) – только буквы и символ «-», первая буква большая.
- Адрес электронной почты (не обязательное поле) – шаблон « ___@___.___ ».
- Номер телефона (обязательное поле).
- Дата рождения, в виде календарной сетки, чтобы нельзя было ввести не существующие даты, например «55 января» (обязательное поле).
- Марка авто (обязательно поле) – выпадающий список с 5 значениями.

3. Отправить значения формы в Базу данных без перезагрузки страницы.

При записи в БД значений привести номер телефона к виду:
89995555555 - если введено 10 или 11 цифр или +79… (номер был +79600112233, должен стать 89600112233)
88435555555 - если введено 7 цифр (номер был 2112233, должен стать 88432112233).

Если пользователь с таким же номер есть в БД вывести сообщение о том, что пользователь уже создан.

4. Написать простой класс (PHP) для работы с БД.
Класс должен выполнять следующие функции:
- добавление записи в БД;
- изменение записи в БД;
- удаление записи из БД.

### Выполнение задания 1.

Размещено: http://testtask.wotskill.ru/testtask1.php /
Порядок выполнения: по п.1. в README_GitHub.md


## Задание 2 (Дополнительное).

1. Вывести на страницу таблицы со значениями из ранее заполненной таблицы в БД.
___________________________________________________________________________

| Фамилия |	Дата рождения |	Номер телефона |	Email	         | Марка авто |

| Иванов	| 1.1.1970      | 89995554455    |	ivanov@mail.ru | Audi       |

___________________________________________________________________________

2. На страницу добавить 3 кнопки.
- Телефон (выполнение функции сортировки по номеру телефона);
- Фамилия (выполнение функции сортировки по фамилии);
- Дата рождения (выполнение функции сортировки по дате рождения).

3. Настроить пагинацию по 10-15 элементов на странице (без сторонних библиотек).

### Выполнение задания 2.

Размещено: http://testtask.wotskill.ru/testtask2.php /
Порядок выполнения: по п.2. в README_GitHub.md


## Задание 3 (task_1). Обработка и отправка заявки с сайта.

### Необходимо (на основе страницы - шаблона):
* Создать\изменить файлы в папке `site` данного репозитория;
* Выполнить валидацию вводимых пользователем данных средствами JS.
* Написать скрипт для записи рекламных меток на странице `site/index.html`;
* Реализовать передачу данных со всех форм на странице `site/index.html`:
  * `Заказать обратный звонок;`
  * `Рассчет со скидкой.`
* Данные нужно передать в формате JSON, POST-запросом на https://webhook.site.

### Рекламные метки:
[Рекламные метки](https://ru.wikipedia.org/wiki/UTM-%D0%BC%D0%B5%D1%82%D0%BA%D0%B8) должны записыватся в cookies сроком на 3 часа.
При повторных переходах на сайт рекламные метки должны браться с cookies и не должны затираться и менять свое значение.

* utm_source - метка получается из GET-запроса
* utm_medium - метка получается из GET-запроса
* utm_content - метка получается из GET-запроса
* utm_campaign - метка получается из GET-запроса
* utm_term - метка получается из GET-запроса
* referrer - сайт с которого был осуществлен переход на данную страницу

Сгенерировать ссылку с рекламными метками можно [здесь](https://tools.yaroshenko.by/utm.php).

### Формат передачи данных:
```json
{
  "form": {
    "id": "calc_1",
    "page": "https://crm-okna.ru"
  },
  "utm": {
    "utm_source": "yandex",
    "utm_medium": "cpc",
    "utm_campaign": "google-poisk",
    "utm_content": "banner-full",
    "utm_term": "iphone",
    "referrer": "facebook.com"
  },
  "contact": {
    "name": "Иван Иванов",
    "email": "ivanov@mail.ru",
    "phone": "89379995556"
  },
  "fields": {
    "height": 1000,
    "width": 300,
    "profile": "REHAU",
    "number": 2,
    "mechanism": "Раздвижной"
  }
}
```

### Выполнение задания 3.

Размещено: http://testtask.wotskill.ru/site/index.php /
Прим. Данные передаются в файл "\docs\miniapi.php". /
Порядок выполнения: по п.3. в README_GitHub.md


## Задание 4 (task_2). Создать пробный аккаунт [AmoCrm](https://www.amocrm.ru/)


## Задание 5 (task_3). Авторизация в аккаунте AmoCrm через средства API.

1. Написать класс для авторизации в аккаунте AmoCrm, используя официальную [документацию](https://www.amocrm.ru/developers/content/api/auth);
2. Успешно авторизоваться в аккаунте AmoCrm, который был создан в Задании № 4;
3. Реализовать логирование исходящих запросов и полученных ответов.

### Выполнение задания
Размещено: http://testtask.wotskill.ru/login_amocrm.php /
Порядок выполнения: по п.5. в README_GitHub.md


## Задание 6 (task_4). Работа с контактами AmoCrm через API.

#### Работа производится в аккаунте AmoCrm, который был создан в задании № 4, используя данные из отправленной формы задания № 3 и авторизацию из задания № 5.

Конечная цель задания:
  - создать новый контакт в AmoCrm;
  - получить по данным из заявки с сайта ID контакта в AmoCrm.

### План выполнения задания:
[Документация по работе с контактами в AmoCrm](https://www.amocrm.ru/developers/content/api/contacts).

Для поиска контактов используется параметр **query**.

1. Осуществить поиск контактов в аккаунте AmoCrm по номеру телефона, без учета двух первых цифр. Получить ID первого контакта, у которого номер телефона в поле соотвествует поисковому номеру;
2. Если контакт не был найден по номеру телефона, то осуществить его поиск по e-mail. Получить ID первого контакта, у которого e-mail в поле соотвествует поисковому e-mail'у;
3. Если контакт не был найден в системе, его нужно создать, заполнив необходимые поля:
 - Имя контакта (name);
  - Мобильный телефон контакта (custom field MOB);
  - E-mail контакта (custom field WORK).


### Выполнение задания
Размещено: http://testtask.wotskill.ru/index.php /
Порядок выполнения: по п.6. в README_GitHub.md


## Задание 7 (task_5). Работа со сделками AmoCrm через API.

#### Работа производится в аккаунте AmoCrm, который был создан в задании № 4, используя данные из отправленной формы задания № 3 и авторизацию из задания № 5, с использованием ID контакта полученного из задания № 6

Конечная цель задания:
  - создать новую сделку в AmoCrm;
  - получить по данным из заявки с сайта ID сделки в AmoCrm.

[Документация по работе со сделками в AmoCrm](https://www.amocrm.ru/developers/content/api/leads).

### План выполнения задания:

1. Необходимо создать дополнительные поля в сделке AmoCrm:
    - **utm_source** - текстовое поле;
    - **utm_medium** - текстовое поле;
    - **utm_content** - текстовое поле;
    - **utm_campaign** - текстовое поле;
    - **utm_term** - текстовое поле;
    - **referrer** - текстовое поле;
    - **ВЫСОТА, ММ**  - текстовое поле;
    - **ШИРИНА, ММ** - текстовое поле;
    - **ПРОФИЛЬ** - списковое поле, значения:
        1. REHAU;
        2. VEKA;
        3. KBE;
        4. KRAUSS;
        5. SALAMANDER.
    - **КОЛ-ВО КАМЕР** - списковое поле, значения:
        1. 2 камеры;
        2. 3 камеры.
    - **МЕХАНИЗМ** - списковое поле, значения:
        1. Поворотный;
        2. Поворотно-откидной;
        3. Раздвижной.
    - **web-site** - мультисписковое поле, значения:
        1. Наименование вашего домена с сайтом окон из задания № 1;
        2. Не задан.
2. Сгруппировать поля c рекламными метками в блок полей **LEAD INFO**, [образец](https://yadi.sk/i/Pv1R88q_G0LagQ);
3. Создать сделку в AmoCrm с необходимыми параметрами:
    - Наименование сделки = *Заявка с сайта **{web-site}** от 12.09.2019*, где *web-site* - наименование домена, с которого пришла заявка;
    - Ответственный за сдеку = любой пользователь, кроме администратора;
    - Заполнить поля из п. 1 данными из заявки с сайта;
    - Прикрепить к сделке контакт, полученный в задании № 4.


### Выполнение задания
Размещено: http://testtask.wotskill.ru/index.php /
Порядок выполнения: по п.6. в README_GitHub.md


## Задание 8 (task_6). Работа с задачами AmoCrm через API.

#### Работа производится в аккаунте AmoCrm, который был создан в задании № 4, используя данные из отправленной формы задания № 3 и авторизацию из задания № 5, с использованием ID контакта полученного из задания № 6 и ID сделки из задания № 7.

Конечная цель задания
  - создать новую задачу в AmoCrm;
  - добавить новую задачу в сделку AmoCrm.

[Документация по работе с задачами в AmoCrm](https://www.amocrm.ru/developers/content/api/tasks).

### План выполнения задания:

1. **Создать новый тип задачи в AmoCrm** - *Заявка с сайта*;
2. **После получения ID сделки в AmoCrm создать задачу с параметрами:**
    - **Тип задачи** = *Заявка с сайта;*
    - **Сущность** = *сделка;*
    - **ID сущности** = *ID созданной сделки;*
    - **Текст задачи** = *<br>"Поступила заявка с сайта **{web-site}**.<br>1) Необходимо связаться с клиентом.<br>2) Затем перевести сделку на следующий этап."<br>где *web-site* - наименование домена, с которого пришла заявка;*
    - **Дата, до которой необходимо завершить задачу** = *задача должна стать просроченной через **15 минут.***


### Выполнение задания
Размещено: http://testtask.wotskill.ru/index.php /
Порядок выполнения: по п.6. в README_GitHub.md


## Задание 9 (task_7). Работа с примечаниями AmoCrm через API.

#### Работа производится в аккаунте AmoCrm, который был создан в задании № 4, используя данные из отправленной формы задания № 3 и авторизацию из задания № 5, с использованием ID контакта полученного из задания № 6 и ID сделки из задания № 7.

Конечная цель задания - добавить новое примечание в сделку AmoCrm.

[Документация по работе с примечаниями в AmoCrm](https://www.amocrm.ru/developers/content/api/notes).

### План выполнения задания:

1. После успешно созданной задачи в сделке необходимо создать примечание с параметрами:
    - **Тип примечания** = *Обычное примечание*;
    - **Сущность** = *сделка;*
    - **ID сущности** = *ID созданной сделки;*
    - **Текст примечания** = *Полная информация о заявке с сайта*, [пример.](https://yadi.sk/i/LgJhGZX9jIa2lw)


### Выполнение задания
Размещено: http://testtask.wotskill.ru/index.php /
Порядок выполнения: по п.6. в README_GitHub.md
