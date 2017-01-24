---
title: "__alignof 運算子 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__alignof"
  - "alignof"
  - "alignas"
  - "__alignof_cpp"
  - "alignof_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__alignof 關鍵字 [C++]"
  - "alignas"
  - "結構的對齊"
  - "alignof"
  - "類型 [C++], 對齊需求"
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __alignof 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+11 引進 `alignof` 運算子，以傳回所指定類型的對齊 \(位元組\)。  若要獲得最高可攜性，您應該使用 alignof 運算子，而不是 Microsoft\-specific \_\_alignof 運算子。  
  
 **Microsoft 特定的**  
  
 傳回 **size\_t** 類型的值，這是類型的對齊需求。  
  
## 語法  
  
```  
  
        __alignof(   
   type    
)  
```  
  
## 備註  
 例如:  
  
|運算式|值|  
|---------|-------|  
|**\_\_alignof\( char \)**|1|  
|**\_\_alignof\( short \)**|2|  
|**\_\_alignof\( int \)**|4|  
|**\_\_alignof\( \_\_int64 \)**|8|  
|**\_\_alignof\( float \)**|4|  
|**\_\_alignof\( double \)**|8|  
|**\_\_alignof\( char\* \)**|4|  
  
 `__alignof` 值與基本類型之 `sizeof` 的值相同。  不過，請考慮這個範例：  
  
```  
typedef struct { int a; double b; } S;  
// __alignof(S) == 8  
```  
  
 在這個案例中，`__alignof` 值是結構中最大項目的對齊需求。  
  
 同樣地，針對  
  
```  
typedef __declspec(align(32)) struct { int a; } S;  
```  
  
 `__alignof(S)` 等於 `32`。  
  
 `__alignof` 的其中一種用法會是做為您其中一個記憶體配置常式的參數。  例如，假設有下列定義的結構 `S`，您可以呼叫名為 `aligned_malloc` 的記憶體配置常式，至特定對齊界限上配置記憶體。  
  
```  
typedef __declspec(align(32)) struct { int a; double b; } S;  
int n = 50; // array size  
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));  
```  
  
 如需修改對齊的詳細資訊，請參閱：  
  
-   [pack](../preprocessor/pack.md)  
  
-   [align](../cpp/align-cpp.md)  
  
-   [\_\_unaligned](../cpp/unaligned.md)  
  
-   [\/Zp \(結構成員對齊\)](../build/reference/zp-struct-member-alignment.md)  
  
-   [結構對齊範例](../build/examples-of-structure-alignment.md) \(x64 專用\)  
  
 如需適用於 x86 和 x64 之程式碼中的對齊差異的詳細資訊，請參閱：  
  
-   [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)  
  
## END Microsoft 特定的  
  
## 請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)