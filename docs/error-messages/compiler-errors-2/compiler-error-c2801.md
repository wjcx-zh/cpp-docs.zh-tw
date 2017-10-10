---
title: "編譯器錯誤 C2801 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2801
dev_langs:
- C++
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 41e7956ace6c54cd55a2ed9f68f18c867bc80ad9
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2801"></a>編譯器錯誤 C2801
'operator operator' 必須是非靜態成員  
  
 下列運算子可以多載只能以非靜態成員：  
  
-   指派`=`  
  
-   類別成員存取`->`  
  
-   Subscripting`[]`  
  
-   函式呼叫`()`  
  
 可能的 C2801 原因：  
  
-   多載的運算子不是類別、 結構或等位成員。  
  
-   宣告多載的運算子`static`。  
  
-   下列範例會產生 C2801:  
  
```  
// C2801.cpp  
// compile with: /c  
operator[]();   // C2801 not a member  
class A {  
   static operator->();   // C2801 static  
   operator()();   // OK  
};  
```
