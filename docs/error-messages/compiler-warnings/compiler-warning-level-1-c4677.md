---
title: 編譯器警告 （層級 1） C4677 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4677
dev_langs:
- C++
helpviewer_keywords:
- C4677
ms.assetid: a8d656a1-e2ff-4f8b-9028-201765131026
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3511ad3100bf695cec5df97703b39e5926c71c11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4677"></a>編譯器警告 (層級 1) C4677
'function': 非私用成員簽章含有組件私用類型 'private_type'  
  
 具有公用存取範圍，在組件外部的型別會使用具有私用組件外部存取的類型。 參考公用組件類型的元件不能使用的型別成員或成員參考之組件私用類型。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4677。  
  
```  
// C4677.cpp  
// compile with: /clr /c /W1  
delegate void TestDel();  
public delegate void TestDel2();  
  
public ref class MyClass {  
public:  
   static event TestDel^ MyClass_Event;   // C4677  
   static event TestDel2^ MyClass_Event2;   // OK  
};  
```