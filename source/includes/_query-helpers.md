# Query Helpers

Our API supports different kind of conditions, at the moment we have a limited set of conditions and they only work as 'AND' conditions not 'OR' conditions... yet!

Here are all the examples of conditions you could do in the platform when you query a list of records and you want to limit the responses with certain conditions you are looking for.


Condition       | Example                           | Query param
-------------   | ---------------------             | ------------------------
where_          | where_identifier                  | { where_identifier: 'text_here' }
in_             | in_type                           | { in_type: ['available', 'waiting_for_ingredients'],}
like_           | like_name                         | { like_name: 'chicken'}
wherenot_       | wherenot_category                 | { wherenot_category: 'grains_bowl_category' }
where<_         | where<_capacity                   | { where<_capacity: 10 }
where>_         | where>_currentLoad                | { where>_currentLoad: 5}
where<=_        | where<=_capacity                  | { where<=_capacity: 5 }
where>=_        | where>=_currentLoad               | { where>=_currentLoad: 5 }
where-not-null_ | where-not-null_inventoryItem      | { where-not-null_inventoryItem: true }
where-null_     | where-null_inventoryItem          | { where-null_inventoryItem: true }
