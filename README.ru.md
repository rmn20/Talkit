# Talkit
Talkit это редактор нелинейных диалогов, работающий через ноды(сеть узлов) и написанный на javascript.
#

Talkit это форк [The Poor Man's Dialogue Tree](http://et1337.com/2014/05/16/the-poor-mans-dialogue-tree/), написанного [et1337](https://github.com/et1337), и являющегося частью проекта [Lemma](https://github.com/et1337/Lemma).. 
Работает через [jointJS](http://www.jointjs.com/) и экспортирует в готовый для игры JSON файл.
![alt text](http://i.imgur.com/7lu8NIy.png?1)

## Виды нодов
### Start
Узел, обозначающий начало диалога

### Text
Отображает текст от определённого персонажа
Actor: Имя персонажа
Speech: Речь персонажа

### Choice
Предназначен для создания диалогов с возможностью выбора ответа
Title: Название варианта ответа, оно может пригодится, если нужно сделать вариант ответа, который отличается от того, который выбирает игрок
Speech: Текст, который говорит персонаж 

### Set
Устанавливает значение переменной. Может вести к одному Text, Node, Set, или Branch.

### Branch
Определяет путь диалога в зависимости от значения переменной. Каждый выход может вести к одному Text, Node, Set, или Branch.

### GenChoice
Создаёт список с различными вариантами ответа, однако варианты ответа появляются только в том случае, если выполнены необходимые условия.
Первый выход идёт по пути, в котором ни одно из условий не соблюдено и ни один из вариантов ответа не появился.
Title: Заголовок экрана выбора
Condition: Условия, необходимые для появления ответа
Choice text: Текст ответа

### Node
Ничего не делает. Может вести к одному Text, Node, Set, Branch, или к некоторому количеству узлов Choice.

## Использование
Запускайте HTML файл, делайте свой диалог и экспортируйте его. 
Вы можете добавить ?load="file.json" к URL для загрузки диалога сохранённого в кеше.  
Пример диалога после экспорта:
```javascript
[
    {
        "type": "Text",
        "id": "227b6f95-2759-4bda-8364-3bcbcb2cbf4d",
        "actor": "Detective",
        "name": "Now tell me Victor.\nWhere were you last night?",
        "choices": [
            "b24806af-4923-4881-84c8-93426cbe3c19",
            "69261cd7-1cfe-4088-8c7c-99f19bc5fb25"
        ]
    },
    {
        "type": "Choice",
        "id": "69261cd7-1cfe-4088-8c7c-99f19bc5fb25",
        "title": "Honest Answer",
        "name": "I was at her house.\nBut I dind't saw anything strange.",
        "next": "6e9f9c69-3efc-447b-ac3a-ade28635b106"
    },
    {
        "type": "Choice",
        "id": "b24806af-4923-4881-84c8-93426cbe3c19",
        "title": "Lie",
        "name": "",
        "next": "fe9c4ac5-3f5a-4df1-91fe-e45b523017d7"
    },
    {
        "type": "Set",
        "id": "6e9f9c69-3efc-447b-ac3a-ade28635b106",
        "variable": "Honest",
        "value": "true",
        "next": "fd3067f6-2afc-42e8-a697-2bb5739a8438"
    },
    {
        "type": "Set",
        "id": "fe9c4ac5-3f5a-4df1-91fe-e45b523017d7",
        "variable": "Honest",
        "value": "false",
        "next": "fd3067f6-2afc-42e8-a697-2bb5739a8438"
    },
    {
        "type": "Text",
        "id": "fd3067f6-2afc-42e8-a697-2bb5739a8438",
        "actor": "Detective",
        "name": "That will be all for now.",
        "next": null
    }
]
```

## Всё ещё не реализовано - TODO:.
* Добавление ?import="file.json" для загрузки диалога с диска.
* Отображение Id нода на каждом ноде.

