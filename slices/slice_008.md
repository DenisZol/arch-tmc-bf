## #бухарх_срез_008 — Состояние системы на сейчас

---

### 🔹 **Цель системы**

1. **Закрыть все старые кейсы** (восстановить проводки, документы, бумажный архив).

2. **Вести учёт дальше правильно и надёжно**, готовым к любой проверке.

3. Переложить **всю рутину на сервер**, оставить людям только ввод данных.

---

### 🔹 **Главные роли**

| Роль           | Обязанности                                                             |
| -------------- | ----------------------------------------------------------------------- |
| Ты             | Заполняешь таблицы, думаешь, принимаешь решения                         |
| Второй человек | Делает сложные акты                                                     |
| Сол            | Строит архитектуру, пишет инструкции, следит за логикой                 |
| Сервер         | Делает проводки, генерирует документы, ставит статус `готов к закрытию` |

---

### 🔹 **Кейс — что это**

> **Кейс** = совокупность поступления, хранения, выдачи ТМЦ, оформленная как логически завершённая единица.

**Формат `case_id`:**  
`донор_описаниеТМЦ_месяц_год`  
🔹 Пример: `UNICEF_шкарпетки_03_2024`

---

### 🔹 **Типы поступлений**

1. **Гуманитарка** → декларация, инвойс, акт приёма

2. **Благотворительность** → акт приёма

3. **Грант** → поступление денег → закупка → приход ТМЦ → выдача

4. **Хозяйственные закупки** → закупки для офиса и структуры

Все ТМЦ **всегда проходят через склад**.  
Сервер определяет тип поступления по явной метке в строке и применяет соответствующую логику учёта.

---

### 🔹 **Жизненный цикл кейса**

| Состояние                     | Условия                                         |
| ----------------------------- | ----------------------------------------------- |
| **Создание кейса**            | Возможна в любой точке: приход, выдача, финансы |
| **Статус “не закрыт”**        | Любой блок кейса ещё пустой (не подтверждён)    |
| **Статус “готов к закрытию”** | Все блоки = “твёрдые”, остатки = 0              |
| **Статус “закрыт”**           | Ставится вручную или по управляющей команде     |
| **Статус “задним числом”**    | Ставится сервером по управляющему файлу         |
| **Статус “ошибка”**           | Странности (например, акт в минус)              |

📌 Сервер сам **не может закрыть кейс**, только предложить.

---

### 🔹 **Что считается твёрдым**

| Элемент   | Критерий твёрдости            |
| --------- | ----------------------------- |
| Акт       | Бумага есть + галочка в Excel |
| Документы | Отмечены в таблице            |
| Остатки   | Выданы или списаны            |

📌 Всё, что не твёрдое — считается пустым.

---

### 🔹 **Документы и бумажный контроль**

| Документ           | Где живёт                                           | Как контролируется    |
| ------------------ | --------------------------------------------------- | --------------------- |
| Акт                | Бумажный архив                                      | В Excel стоит галочка |
| Декларация, инвойс | Только бумага                                       | Пока не фиксируем     |
| Статус документа   | По принципу: либо есть (твёрдое), либо нет (пустое) |                       |
| Архив              | Будет отдельный разговор                            | Отложено              |

---

### 🔹 **Работа с Google Таблицами**

| Форма                 | Состояние                                |
| --------------------- | ---------------------------------------- |
| Excel / Google Sheets | Основной источник данных                 |
| Ввод данных           | Делается вручную человеком               |
| Отметки и статусы     | Вручную или формулами                    |
| Сервер / Сол          | Не вносят данные, а читают, подсказывают |

---

### 🔹 **Порядок закрытия кейса задним числом**

| Этап | Суть                                                                           |
| ---- | ------------------------------------------------------------------------------ |
| 1    | Ты и я выбираем старый кейс                                                    |
| 2    | Анализируем вход/выход, бумажные данные                                        |
| 3    | Принимаем архитектурное решение по закрытию                                    |
| 4    | Я (Сол) создаю управляющий файл                                                |
| 5    | Ты загружаешь его на сервер                                                    |
| 6    | Сервер генерирует документы, вносит строки с пометкой `сгенерировано сервером` |
| 7    | Ты распечатываешь, получаешь подписи                                           |
| 8    | Ставишь галочку — акт становится “твёрдым”                                     |

---

### 🔹 **Журнальная система: контроль исполнения**

| Файл                | Содержит                 | Кто создаёт | Зачем нужен                 |
| ------------------- | ------------------------ | ----------- | --------------------------- |
| 📘 Управляющий файл | Что должно быть сделано  | Сол         | Задаёт структуру и контроль |
| 📙 Журнал сервера   | Что было реально сделано | Сервер      | Аудит и сверка              |

🧮 Программа сверки (контрольный модуль):

- Сравнивает управляющий и журнал;

- Помечает: `выполнено / не выполнено / отклонение`;

- Выводит отчёт.

---

### 🔹 **Принципы**

- Всё, что не твёрдое — считается пустым;

- Кейс можно завести с “конца” (например, с акта);

- Сервер **не закрывает кейсы**, только предлагает;

- Бумажные документы обязательны — без подписи = нет документа;

- Все действия в прошлом отмечаются как “задним числом”;

- Финансы — пока **вне фокуса**. Их учёт отложен.
