---
title: 編譯器錯誤 C2801 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2801
dev_langs:
- C++
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f68b3f575fcb8b909f58ac2ffbcaca26580279da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33237084"
---
# <a name="compiler-error-c2801"></a>編譯器錯誤 C2801
'operator operator' 必須是非靜態成員  
  
 下列運算子可以多載只能以非靜態成員：  
  
-   指派 `=`  
  
-   類別成員存取 `->`  
  
-   Subscripting `[]`  
  
-   函式呼叫 `()`  
  
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