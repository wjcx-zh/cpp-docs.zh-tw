---
title: "void （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
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
caps.latest.revision: 9
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
ms.openlocfilehash: dea06f16979fab9aa4494b172d6d95193a9f3727
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="void-c"></a>void (C++)
做為函式傳回類型時，`void` 關鍵字指定該函式不會傳回值。 用於函式參數清單時，void 指定函式不接受參數。 當用於指標的宣告，void 指定指標是「通用的」。  
  
 如果指標的類型是**void \* **，指標可以指向任何不以宣告的變數**const**或`volatile`關鍵字。 除非它轉換為其他類型，否則 void 指標無法取值。 Void 指標可以轉換成任何其他類型的資料指標。  
  
 Void 指標可以指向函式，但是不能指向 C++ 的類別成員。  
  
 您不能宣告 void 類型的變數。  
  
## <a name="example"></a>範例  
  
```  
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
