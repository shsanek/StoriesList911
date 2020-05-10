# 911
Текстовая игра. Где надо пройти по графу выборов ответов и найти правильный путь.

## Stories
В игре будет много историй каждый из которых представляет граф с переходами между вершинами по экшену.

## Список доступных историй 
Путь: `Stories/StoriesList.json`

## Story
``` json
    {
        "title": "story_name",
        "url": "raw.github.com...."
    }
```
`title` - название истории для списка <br/>
`url` - урл по которому лежит json c историей <br/>

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
    "text": "Message Text"
}
```

`author`[optional] - от кого сообщение простое текстовое поле <br/>
`text`[optional] - текст соообщения <br/>

### Action
Описание перехода между вершинами граффа.
``` json
{
    "node": "node_identifier",
    "text": "button text",
    "dialog": {
        "author": "Äutor",
        "text": "Message Text"
    }
}
```
`text` - текст который будет отображаться на кнопке <br/>
`node` - идентификатор вершины графа на которую нужно перейти <br/>
`dialog` [optional] - сообщение которое останеться после нажатия кнопки (если в диалоге не указан автор будет использоваться action.text если не указан автор то по умолчанию self (если диалога нет то то будет использоваться self action.text))<br/>

### StoryNode
Это вершина граффа
``` json
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
```
`id` - идентификатор вершины графа <br/>
`dialogs` - список диалогов которые будут выведены начиная с первого <br/>
`actions` - список Actions будут выведены как кнопки <br/>

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


