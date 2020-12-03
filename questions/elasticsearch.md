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

### What is an index?

An index refers, in comparison, to a collection in a database.

### What is a shard? 
The shards are pieces of information where Elasticsearch distributes the information. Each document in an index belongs to a primary shard and a replica is a copy of this primary shard.

In summary, the shards are the documents that cointain smaller pieces of information. It cointains a small part of the information of the index so it can be more easy to search through it.

### How does Elasticsearch distribute the information between shards/replicas?

Indexes distribute the information in shards, replicas are not used to distribute information. The replicas are just copies of the primary shards.

An index distributes the information in shards, elasticsearch tries to balance them. They can be rebalanced by modifiying the router but usually elasticsearch tries to keep a balance of how many information is in the shards.

### Replicas

The number of replicas refers to the number of “backups” that the database, in this case, backups of the shards, will have. The replicas have as purpose, assure the availability. 

### How they assure availability?

They cointain the same information as the primary shards, but they can not be modify. They are use to read information and release work on the primary shards. Also, they provide protection againts hardware failure.

By indicating the number of replicas in the settings we indicate the times an index will be backed up. By default, the number of replicas is 1. 


### Number of replicas 
The number of replicas can be dynamically updated by updating the settings of an index 

The settings can be updated by the PUT request with the target and the word _settings  
```
PUT /<target-index>/_settings 
````

Replicas provide redundant copies of your data to protect against hardware failure and increase the capacity to serve read requests like searching or retrieving a document. It is only possible to write in a primary shard, but replicas can be used to read information. 

### What happen when add or substract a replica in number of replicas?
 
 The replicas can be dynamically changed. If added, a new replica of the index is created.
 When a replica is substracted, it is just deleted without any harm to the primary shard.
