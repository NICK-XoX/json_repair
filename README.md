 

This package fixes and cleans up json str responses from ai, handle all broken, misspelled, bracket, issue I have ran into with AIs.

# How to use

Install the library with pip
```bash
pip install git+https://github.com/NICK-XoX/json_repair.git@main#egg=json_repair
```

then you can use use it in your code like this

```python
import json_repair

schema = {
    'type': 'object',
    'properties': {
        'name': {'type': 'string'},
        'description': {'type': 'string'},
        'compeditors': {'type': 'array', 'items': {'type': 'string'}}
    },
    'required': ['name', 'description', 'compeditors']
}

json_str = """ <s> [/s]    ['description', 'name], { "name": "asd", "descriptiond": "asda.", "compediteers": [asd] } more garbage"""

schema_matched_obj = json_repair.comply_schema(json_str, schema)
print(schema_matched_obj)
print(type(schema_matched_obj))
```
```bash
> {'name': 'asd', 'description': 'asda.', 'compeditors': ['asd']}
> <class 'dict'>
```

## Fixes
* misspelled keys
* broken json
* added objects
