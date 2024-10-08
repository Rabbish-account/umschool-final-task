# Финальный проект: Телеграм-бот для знакомств
---
### Цель проекта
---
Вам нужно создать приложение для знакомств используя любую реляционную базу данных (на курсе была PostgreSQL), а также телеграмм, как посредник между клиентом (конечным пользователем) и программой (сервером).

### Требования
___
* Приложение должно иметь разделение на админов (набор telegram IDов) и простых пользователей (всех остальных)
* Приложение должно использовать состояния
* Приложение должно иметь как минимум две связных таблички (чтобы в коде были не просто select/update/insert, а ещё и join).
Вместо написания "сырых" sql запросов можно использовать какую-нибудь ORM, например (https://www.sqlalchemy.org/)
* Пользователь может вставить больше 1 или больше фото в свою анкету
* Основные функции, которые должны быть у пользователя:
    * Смотреть анкеты
    * Моя анкета ( вывод информации о своей анкете )
    * Я больше не хочу никого искать ( эта функция сделает так, чтобы пользователь больше не появлялся в ленте знакомств)
    * Поставить лайк анкете ( Человеку, которому поставили лайк - придёт сообщение о том, что его лайкнули и ссылка на того, кто этот лайк поставил )
    * Поставить дизлайк анкете ( идёт просто переход к анкете следующего человека )
    * Изменить свою анкету
    * Пожаловаться на анкету

* Основные функции администратора
    * Посмотреть жалобы
        * Далее идёт поочередный вывод анкет, на которые пожаловались и текст о жалобе
    * Возможность банить пользователя по его TelegramId
    * Возможность удалять анкету, на которую пожаловались
    * Кнопка переключения на админ режим и режим пользователя
    

    P.S вы уже догадываетесь, в каком боте вы можете подглядеть интерфейс и функционал )

### Примерная структура базы данных
---
Таблица пользователей

| TelegramID (int)|
|-----------------|
|179042112        |
|195302134        |

Таблица анкет

|id (bigint) (PK)|TelegramID (FK)|Name (varchar)|Age (smallint)|Description (varchar)|
|----------------|---------------|--------------|--------------|---------------------|
|1               |179042112       |Vanya         |19            |Love cakes           |
|2               |195302134       |Ilya          |25            |Have a lambo         |

Таблица фотографий

|id (bigint)|AnketaID (FK)|PathPhoto (varchar)|
|-----------|-------------|-------------------|
|1          |2            |(path)             |
|2          |1            |(path)             |

Таблица администраторов

|TelegramID (FK)|
|---------------|
|58182418       |
|51258185       |

Таблица забаненных пользователей
|TelegramID (FK)|
|---------------|
|143243231      |
|232132141      |

# Жесткий дисклеймер. Это всё лишь пожелания, отходить от них можно, просто так будет чуть больше ясности что хочется видеть в результате :)