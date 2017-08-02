# Delete all the keys of the currently selected DB
    127.0.0.1:6379>FLUSHALL  or flushall
    
# select database

the number of databases is defined in the configuration file with the databases directive (the default value is 16). To switch between the databases, call SELECT.
    127.0.0.1:6379>select <1>
    
# DataType
```    
    DataType type = redisTemplate.type(key);  
             if(DataType.NONE == type){                 
                 return null;  
             }else if(DataType.STRING == type){  
                 return super.redisTemplate.opsForValue().get(key);  
             }else if(DataType.LIST == type){  
                 return super.redisTemplate.opsForList().range(key, 0, -1);  
             }else if(DataType.HASH == type){  
                 return super.redisTemplate.opsForHash().entries(key);  
             }else  
                 return null;  
```
