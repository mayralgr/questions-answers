# How does number_of_replicas work?  

```
curl -X PUT "localhost:9200/customer/_settings?pretty" -H 'Content-Type: application/json' -d' 
{ 
     "index" : { 
         "number_of_replicas" : 2 
     } 
}
```

The `_settings` are the settings of Elasticsearch configuration of an index. In the settings of an index, the number of shards and replicas can be defined.  

An index refers, in comparison, to a collection in a database.  

The shards are pieces of information where Elasticsearch distributes the information. Each document in an index belongs to a primary shard and a replica is a copy of this primary shard. 

The number of replicas refers to the number of “backups” that the database, in this case, backups of the shards, will have. The replicas have as purpose, assure the availability. 

By indicating the number of replicas in the settings we indicate the times an index will be backed up. By default, the number of replicas is 1. 

The number of replicas can be dynamically updated by updating the settings of an index 

The settings can be updated by the PUT request with the target and the word _settings  
```
PUT /<target-index>/_settings 
````

Replicas provide redundant copies of your data to protect against hardware failure and increase the capacity to serve read requests like searching or retrieving a document. It is only possible to write in a primary shard, but replicas can be used to read information. 

 