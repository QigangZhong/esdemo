PUT /website/blog/3
{
  "title": "My first blog entry333",
  "text": "Just trying this out...",
  "date": "2014/01/01"
}

GET /website/blog/123

GET /_mget
{
   "docs" : [
      {
         "_index" : "website",
         "_type" :  "blog",
         "_id" :    3
      },
      {
         "_index" : "website",
         "_type" :  "blog",
         "_id" :    1,
         "_source": "title"
      }
   ]
}

GET /website/blog/_mget
{
   "docs" : [
      { "_id" : 2 },
      { "_type" : "blog", "_id" :   1 }
   ]
}


GET /website/blog/_mget
{
   "ids" : [ "2", "1" ]
}

POST /_bulk
{ "delete": { "_index": "website", "_type": "blog", "_id": "123" }}
{ "create": { "_index": "website", "_type": "blog", "_id": "123" }}
{ "title":    "My first blog post" }
{ "index":  { "_index": "website", "_type": "blog" }}
{ "title":    "My second blog post" }
{ "update": { "_index": "website", "_type": "blog", "_id": "123", "retry_on_conflict" : 3} }
{ "doc" : {"title" : "My updated blog post"} }


GET /_cat
GET /_cat/health

GET /_search?pretty

