# Redis-Extend

Redis-Extend is a collection of non-native, atomic redis commands that perform specific tasks. 
If you know lua or are interested in redis, please consider contributing an interesting and useful command - or improve the existing.

## Usage
Simply load the command from scripts/ according to 'command.lua'. The commands are described below.
src/ contains the latest redis scripting branch from http://redis.io.
    
## Commands

### INCRTO key1 [key2 ... keyN] value1 [value2 ... valueN]
For each pair (keyX,valueX), sets keyX to the maximum between its value and valueX. Returns a multi bulk with the values of key1 ... keyN after the call.

### MHDEL key1 [key2 ...] field
Remove the same field from several hashes, get the number of values actually removed.

### MHLEN key1 [key2 ...]
Varadic HLEN.

### MHSET key1 [key2 ... keyN] value1 [value2 ... valueN] field
Set the same field in several hashes, get the number of fields actually created (not updated).

### PATTERNOP pattern operation
Perform 'operation' (eg DEL) on all keys matching 'pattern'

### SISSUBSET key1 key2 
Determine if the set at 'key2' is a subset of the set at 'key1'

### SOPSCARD key1 [key2 ... keyN] operation
The cardinality of the set resulting from the 'operation' (smembers/sinter/sunion) between the sets at 'key1' ... 'keyN'.

### SOPSRANDSUBSET key1 [key2 ... keyN] operation count
A random subset of maximum size 'count' from the 'operation' (smembers/sinter/sunion) between the set at 'key1' and all the sets at 'key2' ... 'keyN'.

### SOPSRANDSUBSTORE key1 [key2 ... keyN] operation count destination
Store a random subset of maximum size 'count' from the 'operation' (smembers/sinter/sunion) between the set at 'key1' and all the sets at 'key2' ... 'keyN' at a key 'destination'