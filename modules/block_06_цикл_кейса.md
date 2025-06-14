**6. Жизненный цикл кейса**

📥 Принято:

| Статус             | Когда применяется                                          |
| ------------------ | ---------------------------------------------------------- |
| `пустой`           | Любой блок кейса не собран или не подтверждён              |
| `готов к закрытию` | Все данные собраны, документы "твёрдые", остатки = 0       |
| `закрыт`           | Ставится вручную или по управляющей команде                |
| `задним числом`    | Ставится сервером при запуске закрытия по прошлым событиям |
| `ошибка`           | Странности: акты в минус, дубли, расхождения               |

📌 Переходы между статусами — **автоматизированы**, кроме `закрыт` (только по команде).

🔍 Вопрос:

- Добавлять ли временный статус типа `в работе` для длинных кейсов, где идут передачи?

- Что с кейсами с остатками, которые “висят” годами?
