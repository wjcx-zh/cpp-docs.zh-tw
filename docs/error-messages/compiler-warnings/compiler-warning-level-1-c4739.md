---
title: "編譯器警告 (層級 1) C4739 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4739
dev_langs:
- C++
helpviewer_keywords:
- C4739
ms.assetid: 600873b3-7c85-4cd4-944e-cd8e01bfcbb0
caps.latest.revision: 9
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
ms.openlocfilehash: a3dff6329d5477e295970ff4e6a1ad72b05bb913
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-warning-level-1-c4739"></a>編譯器警告 (層級 1) C4739
變數 'var' 的參考超過了它的儲存空間  
  
 已指派值給變數，但該值大於變數的大小。 記憶體將寫入到變數的記憶體位置以外，因此可能會遺失資料。  
  
 若要解決這個警告，請只將值指派給其大小可容納該值的變數。  
  
 下列範例會產生 C4739：  
  
```  
// C4739.cpp  
// compile with: /RTCs /Zi /W1 /c  
char *pc;  
int main() {  
   char c;  
   *(int *)&c = 1;   // C4739  
  
   // OK  
   *(char *)&c = 1;  
}  
```
