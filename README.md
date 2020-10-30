# urlshortener-notsoeasy  
```cs
"create backend for url shortener using Django and GraphQL"
```  
### Prerequisites  
- activate a virtual environment
- after creating project directory install requirements.txt using  
```python
pip install -r path/to/requirements.txt
```
### Code
run  
```python
python manage.py runserver
``` 
in the project and navigate to the browser https://localhost:8000/graphql to run queries and mutations  

and using the hash id generated  navigate to https://localhost:8000/hash_id to test the shortened url  

### GraphQL Queries and Mutations  

![GraphiQL](https://assets.digitalocean.com/articles/63911/GraphiQL_Interface.png)  
GraphiQl: interface to run GraphQl Statements

#### Query
```GraphQL
query {
  urls {
    id
    fullUrl
    urlHash
    clicks
    createdAt
  }
}

Output
{
  "data": {
    "urls": []
  }
}
```

#### Mutation
```GraphQL
mutation {
  createUrl(fullUrl:"https://google.com/") {
    url {
      id
      fullUrl
      urlHash
      clicks
      createdAt
    }
  }
}


Output
{
  "data": {
    "createUrl": {
      "url": {
        "id": "1",
        "fullUrl": "https://google.com/",
        "urlHash": "077880af78",
        "clicks": 0,
        "createdAt": "2020-01-30T19:15:10.820062+00:00"
      }
    }
  }
}
```
#### Filters and Pagination
```GraphQL
query {
  urls(url:"community") {
    id
    fullUrl
    urlHash
    clicks
    createdAt
  }
}

Output

{
  "data": {
    "urls": [
      {
        "id": "1",
        "fullUrl": "https://www.digitalocean.com/community",
        "urlHash": "077880af78",
        "clicks": 1,
        "createdAt": "2020-01-30T19:27:36.243900+00:00"
      }
    ]
  }
}


query {
  urls(first: 2, skip: 1) {
    id
    fullUrl
    urlHash
    clicks
    createdAt
  }
}

Output

{
  "data": {
    "urls": [
      {
        "id": "2",
        "fullUrl": "https://google.com/",
        "urlHash": "703562669b",
        "clicks": 0,
        "createdAt": "2020-01-30T19:31:10.820062+00:00"
      }
    ]
  }
}

