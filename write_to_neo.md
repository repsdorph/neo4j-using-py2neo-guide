This is how to write. The example is based on http://py2neo.org/2.0/cypher.html, but exstended for my use.

```python
from py2neo import Graph

graph = Graph()
statement = """
  MERGE (person:Person {name:{person_name}}) ON CREATE SET
    person.age = {person_age},
    person.sex = {person_sex}

  RETURN n
  """

tx = graph.cypher.begin()

def add_persons(persons):
    for person in persons:
        tx.append(statement, {
          'person_name': person['name'],
          'person_age': person['age'],
          'person_sex': person['sex']
        })
    tx.process()

add_persons[{'name': 'Homer', 'age': 32, 'sex': 'Male'}, {'name': 'Bart', 'age': 12, 'sex': 'Male'}]

tx.commit()
```

Of interresting stuff, we have: "On create" http://neo4j.com/docs/stable/query-merge.html#_use_on_create_and_on_match who 
sets some information when we create the note, else the variable person just referes to the person we looked up, and can be 
used later on.
