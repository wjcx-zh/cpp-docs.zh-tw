---
title: void （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- void_cpp
dev_langs:
- C++
helpviewer_keywords:
- void keyword [C++]
- functions [C++], void
- pointers, void
ms.assetid: d203edba-38e6-4056-8b89-011437351057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: dbb46302c2ae8834ab9a2a626a3bfb77c41996a2
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39461474"
---
# <a name="void-c"></a>void (C++)
做為函式的傳回型別，當**void**關鍵字會指定函式不會傳回值。 用於函式參數清單時，void 指定函式不接受參數。 當用於指標的宣告，void 指定指標是「通用的」。  
  
 如果指標的類型是`void *`，指標可以指向任何不以宣告的變數**const**或是**volatile**關鍵字。 除非它轉換為其他類型，否則 void 指標無法取值。 Void 指標可以轉換成任何其他類型的資料指標。  
  
 Void 指標可以指向函式，但是不能指向 C++ 的類別成員。  
  
 您不能宣告 void 類型的變數。  
  
## <a name="example"></a>範例  
  
```cpp 
// void.cpp  
void vobject;   // C2182  
void *pv;   // okay  
int *pint; int i;  
int main() {  
   pv = &i;  
   // Cast optional in C required in C++  
   pint = (int *)pv;  
}   
``` 
  
## <a name="see-also"></a>另請參閱  
 [關鍵字](../cpp/keywords-cpp.md)   
 [基本類型](../cpp/fundamental-types-cpp.md)