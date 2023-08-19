## Creating instances

### Creating/connecting db
`use <db_name>`

### Creating collection
`db.createCollection("<collection_name>")`

<hr>

## Inserting data

### insertOne()
```
db.<collection_name>.insertOne({
	"column" : "value",
	"id of something" : "ObjectId("34243242343254t3")" 
})
```
for referencing  other instances or for primary key `ObjectId()` is used
in order to insert field with the specific `_id` field value use `insertedId` key:
```
db.<collection_name>.insertOne({
	"column" : "value",
	"insertedId" : "ObjectId("32gfd2343254tfds3")" 
})
```

### InsertMany()
Similar to `insertOne()` but inserts multiple documents
```
db.<collection_name>.insertMany([
{
	"column" : "value1",
	"insertedId" : "ObjectId("asdf43dfs342lala1")" 
},
{
	"column" : "value2",
	"insertedId" : "ObjectId("asdf43dfs342lala2")" 
}
])
```

## Retrieving data
for retrieving data we use `find` word:
```mongo
db.<collection_name>.find()  
```