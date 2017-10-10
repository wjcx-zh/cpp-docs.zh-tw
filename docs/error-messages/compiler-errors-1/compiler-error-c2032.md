---
title: "編譯器錯誤 C2032 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2032
dev_langs:
- C++
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 81bbe4c9e5242f68a5e0e304858c13c9274c1743
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2032"></a>編譯器錯誤 C2032
'identifier': 不可結構/等位 'structorunion' 的成員函式。  
  
 結構或等位具有 c + + 中，但在 c 中不允許的成員函式若要解決此錯誤，請編譯為 c + + 程式，或移除此成員函式。  
  
 下列範例會產生 C2032:  
  
```  
// C2032.c  
struct z {  
   int i;  
   void func();   // C2032  
};  
```  
  
 可能的解決方式：  
  
```  
// C2032b.c  
// compile with: /c  
struct z {  
   int i;  
};  
```
