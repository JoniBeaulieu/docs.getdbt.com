---
title: "set"
id: "set"
---

### set

_Not to be confused with the `{% set foo = "bar" ... %}` expression in Jinja!_

The `set` context method can be used to convert any iterable to a sequence of iterable elements that are unique (a set).
        
__Args__:
- `value`: The iterable to convert (e.g. a list)
- `default`: A default value to return if the `value` argument is not a valid iterable

### Usage

```
{% set my_list = [1, 2, 2, 3] %}
{% set my_set = set(my_list) %}
{% do log(my_set) %}  {# {1, 2, 3} #}
```

```
{% set my_invalid_iterable = 1234 %}
{% set my_set = set(my_invalid_iterable) %}
{% do log(my_set) %}  {# None #}
```

### try_set

The `try_set` context method can be used to convert any iterable to a sequence of iterable elements that are unique (a set). The difference to the `set` context method is that the `try_set` method will raise an exception on a `TypeError`, if the provided value is not a valid iterable and cannot be converted to a set.

__Args__:
- `value`: The iterable to convert (e.g. a list)

```
{% set my_list = [1, 2, 2, 3] %}
{% set my_set = set(my_list) %}
{% do log(my_set) %}  {# {1, 2, 3} #}
```

```
{% set my_invalid_iterable = 1234 %}
{% set my_set = try_set(my_invalid_iterable) %}
{% do log(my_set) %}

Compilation Error in ... (...)
  'int' object is not iterable
```
