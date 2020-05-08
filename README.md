# 911
Текстовая игра. Где надо пройти по графу выборов ответов и найти правильный путь.

## Stories
В игре будет много историй каждый из которых представляет граф с переходами между вершинами по экшену.

## Список доступных историй 
Путь: `Stories/StoriesList.json`
``` json
    [
        {
            "title": "story_name",
            "url": "raw.github.com...."
        }
    ]
```
`title` - название истории для списка <br/>
`url` - урл по которому лежит json c историей <br/>

## Формат посторояния графа для Story
### Dealog
Это то что игра будет выводить на экран как сообщения

``` json
{
    "autor": "Äutor",
    "text": "Message Text"
}
```

`autor`[optional] - от кого сообщение простое текстовое поле <br/>
`text`[optional] - текст соообщения <br/>

### Action
Описание перехода между вершинами граффа.
``` json
{
    "identifier": "node_identifier",
    "text": "button text",
    "dialog": {
        "autor": "Äutor",
        "text": "Message Text"
    }
}
```
`text` - текст который будет отображаться на кнопке <br/>
`identifier` - идентификатор вершины графа на которую нужно перейти <br/>
`dialog` - сообщение которое останеться после нажатия кнопки <br/>

### StoryNode
Это вершина граффа
``` json
{
    "identifier": "node_identifier",
    "dialogs": [
        {
            "autor": "Äutor",
            "text": "Message Text"
        }
    ],
    "actions": [
        {
            "identifier": "node_identifier",
            "text": "button text",
            "dialog": {
                "autor": "Äutor",
                "text": "Message Text"
            }
        }
    ],
}
```
`identifier` - идентификатор вершины графа <br/>
`dialogs` - список диалогов которые будут выведены начиная с первого <br/>
`actions` - список Actions будут выведены как кнопки <br/>

### Stroy
Модель графа
``` json
{
    "startIdentifier": "node_identifier",
    "title": "button text",
    "nodes": [
        {
            "identifier": "node_identifier",
            "dialogs": [
                {
                    "autor": "Äutor",
                    "text": "Message Text"
                }
            ],
            "actions": [
                {
                    "identifier": "node_identifier",
                    "text": "button text",
                    "dialog": {
                        "autor": "Äutor",
                        "text": "Message Text"
                    }
                }
            ],
        }
    ]
}
```
`title` - название события <br/>
`startIdentifier` - идентификатор вершины графа на которую нужно перейти для начала <br/>
`nodes` - список вершин <br/>


