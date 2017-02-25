---
title: "Variadic 巨集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "variadic 巨集 [C++]"
  - "__VA_ARGS__ variadic 巨集規範"
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Variadic 巨集
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Variadic 巨集（macros）是包含引數的變數數字、類似函式的巨集。  
  
## 備註  
 若要使用 variadic 巨集，省略符號在巨集定義中可能被指定為最終的正式引數，並且取代識別項 `__VA_ARGS__` 在這個定義可用作插入額外的引數。 `__VA_ARGS__` 由符合省略符號的引數取代，包括在它們之間的逗號。  
  
 C 標準指定必須將至少一個引數傳遞給這個省略符號，確保巨集不會將它解析成結尾的逗號。如果沒有傳遞引數至省略符號， Visual C\+\+ 實作時會隱藏一個結尾的逗號。  
  
## 範例  
  
```cpp  
// variadic_macros.cpp  
#include <stdio.h>  
#define EMPTY  
  
#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }  
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }  
#define CHECK3(...) { printf(__VA_ARGS__); }  
#define MACRO(s, ...) printf(s, __VA_ARGS__)  
  
int main() {  
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");  
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print  
  
    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print  
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");  
  
    // always invokes printf in the macro  
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");  
  
    MACRO("hello, world\n");  
  
    MACRO("error\n", EMPTY); // would cause error C2059, except VC++   
                             // suppresses the trailing comma  
}  
```  
  
## Output  
  
```  
here are some varargs1(1)  
here are some varargs2(4)  
here are some varargs3(5)  
hello, world  
error  
  
```  
  
## 請參閱  
 [巨集](../preprocessor/macros-c-cpp.md)