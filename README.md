## Для экзамена по КиТГ

Реализованы следующие алгоритмы:
* Косарайя-Шарира - поиск компонент сильной связности ориентированного графа
* Дейкстры - поиск кратчайших путей
* Флойда - поиск всех кратчайших путей для всех вершин
* Форда–Фалкерсона - поиск максимального потока (без подробного вывода)

Граф считывается из файла graph.json

**NOTE**: Протестировано на нескольких премерах и версии Python 3.7

### Способ задания графа

Граф задаётся через json файл. В json-объекте должны находится следующие значения:
* *oriented* - *true*, если граф ориентированный, иначе *false*
* *nodes* - список вершин графа
* *ribs* - ребра графа

Задание ребёр:
```json
"ribs": {
    "A": ["B", "C"] // Без весов, по умолчанию вес равен 1
    "B": [["E", 5], ["D", -4], "C"] // С весами (можно комбинировать)
}
```

Несколько примеров задания графа:
```json
{
  "oriented": true,
  "nodes": ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L"],
  "ribs": {
    "A": [["E", 4], ["F", 5]],
    "B": [["A",3],["C",7],["F",5]],
    "C": [["B",7],["D",2]],
    "D": [["C",2],["G",2]],
    "E": [["F",8]],
    "F": [["C",2],["E",8], ["G",7], ["J",2]],
    "G": [["F",7],["J",8],["K",8]],
    "H": [["G",3],["L",7]],
    "I": [["E",3],["F",7],["J",4]],
    "J": [["G",8],["I",4],["K",3]],
    "K": [["H",2], ["J",3]],
    "L": [["H",7],["K",2]]
  }
}
```

```json
{
  "oriented": true,
  "nodes": ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N"],
  "ribs": {
    "A": [["B",9], ["C",10], ["D",17]],
    "B": [["E",7], ["F",10]],
    "C": [["E",4],["G",1]],
    "D": [["F",10], ["G",1]],
    "E": [["H",1], ["I",7]],
    "F": [["H",10], ["J",5]],
    "G": [["I",1], ["J",9]],
    "H": [["K",8], ["L", 1]],
    "I": [["K",6], ["M",10]],
    "J": [["L", 10], ["M",9]],
    "K": [["N", 11]],
    "L": [["N", 9]],
    "M": [["N", 19]],
    "N": []
  }
}
```

### Прочее

В файлах ```16_graph.json``` и ```5_graph.json``` находятся заготовки для графов
Версия с одним файлом лежит в папке ```one_file_ver```