---
title: "編譯器錯誤 C2178 |Microsoft 文件"
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2178
dev_langs:
- C++
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
caps.latest.revision: 0
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: facb255b0c53a3de0e1d5c9f90de5835b25e3c32
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2178"></a>編譯器錯誤 C2178  
  
'*識別碼*'不可以宣告與'*規範*' 規範  
  
A`mutable`規範使用在宣告中，但在此內容中不允許規範。  
  
`mutable`規範可以只會套用至類別資料成員的名稱，但不可套用至宣告的名稱`const`或`static`，但不可套用至參考的成員。  
  
## <a name="example"></a>範例  
  
下列範例顯示如何 C2178 可能會發生，以及如何修正此問題。  
  
```  
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```  

