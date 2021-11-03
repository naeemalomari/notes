# Hashtables

## What is a Hashtable?

 Hash - A hash is the result of some algorithm taking an incoming string and converting it into a value that could be used for either security or some other purpose. In the case of a hashtable, it is used to determine the index of the array.
 Buckets - A bucket is what is contained in each index of the array of the hashtable. Each index is a bucket. An index could potentially contain multiple key/value pairs if a collision occurs.
 Collisions - A collision is what happens when more than one key gets hashed to the same location of the hashtable.

## Why do we use them?

1. Hold unique values
2. Dictionary
3. Library

* Hashtables are a data structure that utilize key value pairs. (key ,value)
* The basic idea of a hashtable is the ability to store the key into this data structure, and quickly retrieve the value.
* A hash is the ability to encode the key that will eventually map to a specific location in the data structure that we can look at directly to retrieve the value.
* we are able to hash our key and determine the exact location where our value is stored, we can do a lookup in an O(1) time complexity.
* A hash table can start with only a few buckets, calculate it’s own load factor, recognize when it gets too full and automatically grow and add more buckets to itself to accommodate more data.
* If we know the index of the information we want we can access that information in O(1) time.
* Hash maps take advantage of an array’s O(1) read access. Instead of adding elements to an array from beginning to end, a hash map uses a “hash function” to place each item at a precise index location, based off it’s key.
* The hash code is used again to read something from the hash map

# Structure

## Hashing

* a hash code turns a key into an integer.
* Hash codes should never have randomness to them. The same key should always produce the same hash code.

## Creating a Hash

* A hashtable traditionally is created from an array.
* After you have created your array of the appropriate size, do some sort of logic to turn that “key” into a numeric number value. Here is a possible suggestion:

1. Add or multiply all the ASCII values together.
2. Multiply it by a prime number such as 599.
3. Use modulo to get the remainder of the result, when divided by the total size of the array.
4. Insert into the array at that index.

* to find the index

```Key = "Cat"
Value = "Josie"

67 + 97 + 116 = 280

280 * 599 = 69648

69648 % 1024 = 16

Key gets placed in index of 16. 
```

* We now know that our key Cat maps to index 16 of the array. We can view into this index and find “Josie”, our value quickly.
* Each index of the array can hold many types of values.
* Each index of the array can hold many types of values.
* When there is no entry in a specific bucket, the buckets (each index of the array) all start null.

## Collisions

* A collision occurs when more than one key hashes to the same index in an array.
* a “perfect hash” will never have any collisions.
* the worst possible hash is one that hashes every single key to the same exact index of an array.
* Collisions are solved by changing the initial state of the buckets.
* Instead of starting them all as null we can initialize a LinkedList in each one!

# Hash maps do this to store values

accept a key
calculate the hash of the key
use modulus to convert the hash into an array index
store the key with the value by appending both to the end of a linked list

# Hash maps do this to read value

accept a key
calculate the hash of the key
use modulus to convert the hash into an array index
use the array index to access the short LinkedList representing a bucket
search through the bucket looking for a node with a key/value pair that matches the key you were given

## Bucket Sizes

* Hash Maps can have any number of buckets.
* If a hash map has only a few buckets it will be densely full and have many collisions. If a hash map has more buckets it will be more sparsely populated, there will be less collisions, but there may be a lot of extra empty space.
* Now if two keys resolve to the same index in the array then their key/value pairs can be stored as a node in a linked list.
* Each index in the array is called a “bucket” because it can store multiple key/value pairs.

## Internal Methods

Add()
Find()
Contains()
GetHash()
