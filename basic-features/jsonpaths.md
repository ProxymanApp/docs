# JSONPath

## 1. What's it?

JSONPath is a tool for quickly filtering from JSON data.

![Filter JSON data](../.gitbook/assets/Screen\_Shot\_2021-08-01\_at\_10\_29\_35.png)

### Operator

| Operator                  | Description                                                         |
| ------------------------- | ------------------------------------------------------------------- |
| `$`                       | The root element to query. This starts all path expressions.        |
| `@`                       | The current node is being processed by a filter predicate.          |
| `*`                       | Wildcard. Available anywhere a name or numeric are required.        |
| `..`                      | Deep scan. Available anywhere a name is required.                   |
| `.<name>`                 | Dot-notated child                                                   |
| `['<name>' (, '<name>')]` | Bracket-notated child or children                                   |
| `[<number> (, <number>)]` | Array index or indexes                                              |
| `[start:end]`             | Array slice operator                                                |
| `[?(<expression>)]`       | Filter expression. The expression must evaluate to a boolean value. |

### Filter Operators

Filters are logical expressions used to filter arrays. A typical filter would be `[?(@.age > 18)]` where `@` represents the current item being processed.

| Operator | Description                                                          |
| -------- | -------------------------------------------------------------------- |
| ==       | left is equal to the right (note that 1 is not equal to '1')         |
| !=       | left is not equal to the right                                       |
| <        | left is less than right                                              |
| <=       | left is less or equal to the right                                   |
| >        | left is greater than right                                           |
| >=       | left is greater than or equal to the right                           |
| =\~      | left matches regular expression \[?(@.name =\~ /foo.\*?/i)]          |
| in       | left exists in right \[?(@.size in \['S', 'M'])]                     |
| nin      | left does not exists in right                                        |
| subsetof | left is a subset of right \[?(@.sizes subsetof \['S', 'M', 'L'])]    |
| anyof    | left has an intersection with right \[?(@.sizes anyof \['M', 'L'])]  |
| noneof   | left has no intersection with right \[?(@.sizes noneof \['M', 'L'])] |
| size     | size of left (array or string) should match right                    |
| empty    | left (array or string) should be empty                               |

### Path Examples

Given the JSON Data.

```javascript
{
    "store": {
        "book": [
            {
                "category": "reference",
                "author": "Nigel Rees",
                "title": "Sayings of the Century",
                "price": 8.95
            },
            {
                "category": "fiction",
                "author": "Evelyn Waugh",
                "title": "Sword of Honour",
                "price": 12.99
            },
            {
                "category": "fiction",
                "author": "Herman Melville",
                "title": "Moby Dick",
                "isbn": "0-553-21311-3",
                "price": 8.99
            },
            {
                "category": "fiction",
                "author": "J. R. R. Tolkien",
                "title": "The Lord of the Rings",
                "isbn": "0-395-19395-8",
                "price": 22.99
            }
        ],
        "bicycle": {
            "color": "red",
            "price": 19.95
        }
    },
    "expensive": 10
}
```

| JsonPath                                | Result                                                       |
| --------------------------------------- | ------------------------------------------------------------ |
| $.store.book\[\*].author                | The authors of all books                                     |
| $..author                               | All authors                                                  |
| $.store.\*                              | All things, both books and bicycles                          |
| $.store..price                          | The price of everything                                      |
| $..book\[2]                             | The third book                                               |
| $..book\[-2]                            | The second to last book                                      |
| $..book\[0,1]                           | The first two books                                          |
| $..book\[:2]                            | All books from index 0 (inclusive) until index 2 (exclusive) |
| $..book\[1:2]                           | All books from index 1 (inclusive) until index 2 (exclusive) |
| $..book\[-2:]                           | Last two books                                               |
| $..book\[2:]                            | Book number two from tail                                    |
| $..book\[?(@.isbn)]                     | All books with an ISBN number                                |
| $.store.book\[?(@.price < 10)]          | All books in store cheaper than 10                           |
| $..book\[?(@.price <= $\['expensive'])] | All books in store that are not "expensive"                  |
| $..book\[?(@.author =\~ /.\*REES/i)]    | All books matching regex (ignore case)                       |
| $..\*                                   | Give me everything                                           |
| $..book.length()                        | The number of books                                          |

### Reference

* [https://github.com/json-path/JsonPath](https://github.com/json-path/JsonPath)
