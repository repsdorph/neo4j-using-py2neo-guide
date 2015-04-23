To find a path from one node to other nodes:

```cypher
MATCH path=shortestPath((p:Person)-[:tweeted|in_reply_to|mentions*1..5]->(p2:Person))
WHERE p.twitter_screen_name = "ThomasRepsdorph"
RETURN path
```

Notice the `shortestPath` tag. This make it a lot faster, as it filters on `(p)`, so it only need to have a copy of all `(:Person)` twice.
