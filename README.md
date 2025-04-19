# Catos STL

## Features:
 - [x] String
 - [x] Vector
 - [x] RawVector
 - [x] ~~Hashmap~~
 - [x] Any

## Notes:
- The hashmap is functional however its not production ready and it isnt recommended.
- The String class is missing a bunch of ``to_string`` utility functions


## How to use:

### Vectors
```c++
// You can both initialize a vector with and without arguments
catos::vector<float> empty{};

//Pre allocates the amount of items needed
empty.reserve(4);

empty.push_back(1.0f);
empty.push_back(2.0f);
empty.push_back(3.0f);
empty.push_back(4.0f);

// Vector has iterators
for (auto it : empty) {
    std::cout << it << "\n";
}

catos::vector<float> filled{1.0f, 2.0f, 3.0f, 4.0f};

for (auto it : fill) {
    std::cout << it << "\n";
}
```
### RawVector
RawVectors are vectors that are not depend on templates
its constructor takes a catos::vector.
#### Note: raw_vector is read ONLY!
```c++

catos::vector<float> filled{1.0f, 2.0f, 3.0f, 4.0f};

catos::raw_vector raw{filled};

// The iterator returns a raw pointer to each item in the vector
for (void* ptr : raw) {
    std::cout << *(float*) ptr << "\n";
}

```

### String
```c++

catos::string hello = "Hello ";
catos::string world = "World";

catos::string out = hello + world;

std::cout << out.c_str() << "\n";
```
### Hashmaps
```c++

//Note String are required to have a separate hashfunction
// You can also specify your own hash function 

catos::hashmap<int, int> map;

map.put(1, 2);
map.put(2, 6);
map.put(3, 2);
map.put(4, 7);

// val = 6;
int val = map.get(2);

//Iterating (note: the iterator is not recommend but works :/)
// catos::hashmap::all returns a catos::vector<pair<K, V>>
for (auto pair: map.all()) {
    std::cout << "KEY " << pair.first << " | VAL " << pair.second << "\n";
}

```

### Any
```c++
void print(catos::any value) {
    std::cout << value.get<float>() << "\n";
}

print(1.0f);

// 1.0f
```