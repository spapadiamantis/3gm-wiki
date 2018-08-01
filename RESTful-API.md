# RESTful API 

## API Endpoints

You can access the application data via a _RESTful API_. Below there are some basic endpoints (GET):

```
/get_law/string:statute_type/string:identifier/string:year
```

To get the versions of a law. 

Example: 

```
/get_law/l/4009/2011
```

The `statute_type` can be either `l` for law (ν.) or `pd` for Presidential Decree. 

In the same way you can get the links to the law and its topics. The endpoints (GET) for this are 

```
/get_link/string:statute_type/string:identifier/string:year
/get_topic/string:statute_type/string:identifier/string:year
```

You can also check the syntax api via the resource: 

```
/get_syntax/string:s
```



