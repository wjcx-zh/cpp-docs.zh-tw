---
title: "編譯器警告 （層級 2） C4285 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4285
dev_langs:
- C++
helpviewer_keywords:
- C4285
ms.assetid: fa14de1f-fc19-4eec-8bea-81003636e12f
caps.latest.revision: 6
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: ab81b59a711aa5ed623e2976c3d5eabfea58a5e3
ms.lasthandoff: 04/01/2017

---
# <a name="compiler-warning-level-2-c4285"></a>編譯器警告 (層級 2) C4285
如果使用中置標記法來套用，'-> identifier:: operator' 的傳回型別是遞迴  
  
 指定**operator->()**函式無法傳回的型別它被定義或為其定義的類型的參考。  
  
 下列範例會產生 C4285:  
  
```  
// C4285.cpp  
// compile with: /W2  
class C  
{  
public:  
    C operator->();   // C4285  
   // C& operator->();  C4285, also  
};  
  
int main()  
{  
}  
```
