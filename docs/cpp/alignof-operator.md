---
title: "__alignof 運算子 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __alignof
- alignof
- alignas
- __alignof_cpp
- alignof_cpp
dev_langs:
- C++
helpviewer_keywords:
- alignas
- alignment of structures
- __alignof keyword [C++]
- alignof
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 66ec7ff196a4f22aec043d8b76faf0189e05cd0f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="alignof-operator"></a>__alignof 運算子
C++11 引進 `alignof` 運算子，以傳回所指定類型的對齊 (位元組)。 若要獲得最高可攜性，您應該使用 alignof 運算子，而不是 Microsoft-specific __alignof 運算子。  
  
 **Microsoft 特定的**  
  
 傳回值的型別**size_t**也就是類型的對齊需求。  
  
## <a name="syntax"></a>語法  
  
```  
  
      __alignof(   
   type    
)  
```  
  
## <a name="remarks"></a>備註  
 例如:   
  
|運算式|值|  
|----------------|-----------|  
|**__alignof (char)**|1|  
|**__alignof （短整數）**|2|  
|**__alignof (int)**|4|  
|**__alignof ( \__int64)**|8|  
|**__alignof (float)**|4|  
|**__alignof (double)**|8|  
|**__alignof (char\* )**|4|  
  
 `__alignof` 值與基本類型之 `sizeof` 的值相同。 不過，請考慮這個範例：  
  
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
  
 `__alignof` 的其中一種用法會是做為您其中一個記憶體配置常式的參數。 例如，假設有下列定義的結構 `S`，您可以呼叫名為 `aligned_malloc` 的記憶體配置常式，至特定對齊界限上配置記憶體。  
  
```  
typedef __declspec(align(32)) struct { int a; double b; } S;  
int n = 50; // array size  
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));  
```  
  
 如需修改對齊的詳細資訊，請參閱：  
  
-   [pack](../preprocessor/pack.md)  
  
-   [align](../cpp/align-cpp.md)  
  
-   [__unaligned](../cpp/unaligned.md)  
  
-   [/Zp （結構成員對齊）](../build/reference/zp-struct-member-alignment.md)  
  
-   [結構對齊範例](../build/examples-of-structure-alignment.md)(x64 專用)  
  
 如需適用於 x86 和 x64 之程式碼中的對齊差異的詳細資訊，請參閱：  
  
-   [與 x86 編譯器衝突](../build/conflicts-with-the-x86-compiler.md)  
  
**END Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [具有一元運算子的運算式](../cpp/expressions-with-unary-operators.md)   
 [關鍵字](../cpp/keywords-cpp.md)
