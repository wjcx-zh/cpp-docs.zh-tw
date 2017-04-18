---
title: "編譯器警告 （層級 3） C4646 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4646
dev_langs:
- C++
helpviewer_keywords:
- C4646
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 9fe7c1ca87dd80133e4073f41ad434dd24052db5
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-3-c4646"></a>編譯器警告 (層級 3) C4646
使用 __declspec(noreturn) 宣告的函式有非 void 的傳回類型  
  
 函式標示[noreturn](../../cpp/noreturn.md) `__declspec`修飾詞應該有[void](../../cpp/void-cpp.md)傳回型別。  
  
 下列範例會產生 C4646：  
  
```  
// C4646.cpp  
// compile with: /W3 /WX  
int __declspec(noreturn) TestFunction()  
{   // C4646  make return type void  
}  
```
