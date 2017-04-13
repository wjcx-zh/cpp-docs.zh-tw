---
title: "編譯器警告 （層級 1） C4807 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4807
dev_langs:
- C++
helpviewer_keywords:
- C4807
ms.assetid: 089c9f87-fd81-402e-9826-66a8ef1ef1fe
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
ms.openlocfilehash: 1548905fd242707c1cdf01c2cbc51b5c9e50cfce
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4807"></a>編譯器警告 (層級 1) C4807
'operation' : 不安全的混用類型 'type' 和類型 'type' 的已簽名位元欄位  
  
 比較一位元帶正負號位元欄位與 `bool` 變數時，會產生這個警告。 因為一位元帶正負號位元欄位只能包含值 -1 或 0，所以比較它與 `bool`十分危險。 不會產生有關混合使用 `bool` 與一位元未帶正負號位元欄位的警告，因為它們與 `bool` 相同，而且只能保留 0 或 1。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4807：  
  
```  
// C4807.cpp  
// compile with: /W1  
typedef struct bitfield {  
   signed mybit : 1;  
} mybitfield;  
  
int main() {  
   mybitfield bf;  
   bool b = true;  
  
   // try..  
   // int b = true;  
  
   bf.mybit = -1;  
   if (b == bf.mybit) {   // C4807  
      b = false;  
   }  
}  
```
