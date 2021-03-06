# Overview

## About The Project

Helper library for external windows game hacking.

Collaborative work provided by the <a href="https://discord.gg/CRMQq4F" target="_blank">CasualCommunity</a>

## Documentation

The main set of documentation can be found <a href="https://casualcoder91.github.io/CasualLibrary/html/index.html" target="_blank">here</a>

## Usage

bare-bones setup

```cpp
#include <iostream>
#include "Memory.h"

int main(){
    External::Memory memory = External::Memory("target.exe");
}
```

read/write memory

```cpp
//works for all types including uintptr_t, int, double etc. as well as custom structs and classes.
//does NOT work for arrays/vectors
uintptr_t adress = 0x2240001C;
// read integer stored at address
int test = memory.read<int>(address);
// read one word
std::string word = memory.readString(address);
//read 200 chars
std::string text = memory.readString(address, 200);
//write value 5 starting at given address
memory.write<int>(address, 5);
```

get address from static pointer + offsets

```cpp
uintptr_t healthAddr = memory.getAddress(0x2240001C, { 0x01,0x4E });
```

get module base address

```cpp
uintptr_t clientAddr = memory.getModule(L"client.dll");
```
