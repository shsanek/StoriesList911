# 911
Текстовая игра. Где надо пройти по графу выборов ответов и найти правильный путь.

## StoryHeart
Небольшая утилитка для контроля значений переменных (пока только числовых)

### доступные операторы 
`+ - / *` - базовые ареметические операторы (отсутсвует унарный минус (-x)) <br/>
`== >= <= > <` - операторы сравнения <br/>
`&& || !` - базовые бинарные операторы <br/>
`( )` - оператор выставления приоритетов <br/>
`=` - оператор присваивания <br/>

## переменные 
идентификатор переменой может содержать символы латинского алфавита (с учетом регистра) и знак `_` <br/>
также если перед перемной есть знак `$` -  то переменная будет доступна и после завершения задания (являеться глобальной и сахраняемой)

## некоторые базовые перменные 
`$service_number_of_items_(serviceName)` - количество едениц техники доступное для сервиса serviceName<br/>
`address_position` - количество шагов для проезда к месту истории (если 0 считаеться что адресс не задан)<br/>

`service_in_address_(serviceName)`[неизменяемое] - количество едениц техники которые приехали на адресс serviceName <br/>
`service_move_in_address_(serviceName)`[неизменяемое] - количество едениц техники кооторые едут на адресс serviceName <br/>
`service_hold_(serviceName)`[неизменяемое] - количество едениц техники которые должны вернуться на базу после завершениея задания <br/>
`step`[неизменяемое] - количество шагов от начала задания <br/>
`$step`[неизменяемое] - количество шагов от начала игры <br/>

## service
доступные службы


## Stories
В игре будет много историй каждый из которых представляет граф с переходами между вершинами по экшену.

## Список доступных историй 
Путь: `Stories/StoriesList.json`

## Story
``` json
    {
        "enabled": "bool expression",
        "title": "story_name",
        "url": "subpath",
        "nextStories": ["s1", "s2"]
    }
```
`title` - название истории для списка <br/>
`url` - урл по которому лежит json c историей <br/>
`enabled` - выражение если равно 0 то переход к истории невозможен <br/>
`nextStories` - список историй которые можно выбрать после прохождения этой истории <br/>

## StoriesList
``` json
{
    "stories": [
        {
            "title": "story_name",
            "url": "raw.github.com...."
        }
    ]
}
```
`stories` - массив доступных историй <br/>

## Формат посторояния графа для Story
### Dealog
Это то что игра будет выводить на экран как сообщения

``` json
{
    "author": "Äutor",
    "show": "bool expression",
    "text": "Message Text"
}
```

`author`[optional] - от кого сообщение простое текстовое поле <br/>
`text`[optional] - текст соообщения <br/>
`show` [optional] - выражение если вернуло 0 диалог не будет показан (не работает для диалогов в экшене) <br/>

### Action
Описание перехода между вершинами граффа.
``` json
{
    "enabled": "bool expression",
    "script": "script",
    "node": "node_identifier",
    "text": "button text",
    "dialog": {
        "author": "Äutor",
        "text": "Message Text"
    }
}
```
`enabled `[optional] - выражение , если вернуло 0 экшен не будет показан <br/>
`script` [optional] - скрипт вызывающийся при активации экшена (каждый раз) <br/>
`text` - текст который будет отображаться на кнопке <br/>
`node` - идентификатор вершины графа на которую нужно перейти <br/>
`dialog` [optional] - сообщение которое останеться после нажатия кнопки (если в диалоге не указан автор будет использоваться action.text если не указан автор то по умолчанию self (если диалога нет то то будет использоваться self action.text))<br/>

### StoryNode
Это вершина граффа
``` json
{
    "id": "node_identifier",
    "push": false,
    "dialogs": [
        {
            "autor": "Äutor",
            "text": "Message Text"
        }
    ],
    "actions": [
        {
            "node": "node_identifier",
            "text": "button text",
            "dialog": {
                "author": "Äutor",
                "text": "Message Text"
            }
        }
    ],
}
```
`id` - идентификатор вершины графа <br/>
`activationScript` - скрипт вызываеться при первом заходе в ноду <br/>
`actionScript` - вызываеться при каждом заходе в ноду <br/>
`dialogs` - список диалогов которые будут выведены начиная с первого <br/>
`actions` - список Actions будут выведены как кнопки <br/>
`push` [optional] - если true система запомнит предыдущию ноду и как только не останеться экшенов покажет экшены этой ноды <br/>

### Stroy
Модель графа
``` json
{
    "startNode": "node_identifier",
    "title": "button text",
    "nodes": [
        {
            "id": "node_identifier",
            "dialogs": [
                {
                    "autor": "Äutor",
                    "text": "Message Text"
                }
            ],
            "actions": [
                {
                    "node": "node_identifier",
                    "text": "button text",
                    "dialog": {
                        "author": "Äutor",
                        "text": "Message Text"
                    }
                }
            ],
        }
    ]
}
```
`title` - название события <br/>
`startNode` - идентификатор вершины графа на которую нужно перейти для начала <br/>
`nodes` - список вершин <br/>


