---
title: 編譯器錯誤 C2863 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2863
dev_langs:
- C++
helpviewer_keywords:
- C2863
ms.assetid: 32561d67-a795-486b-b3b6-4b90a1acb176
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 272697a43f99993565fe9af13cde7de29289a93d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2863"></a>編譯器錯誤 C2863
'interface': 介面不能有 friend  
  
 不允許宣告 friend 介面上。  
  
 下列範例會產生 C2863:  
  
```  
// C2863.cpp  
// compile with: /c  
#include <unknwn.h>  
  
class CMyClass {  
   void *f();  
};   
  
__interface IMyInterface {  
   void g();  
  
   friend int h();   // 2863  
   friend interface IMyInterface1;  // C2863  
   friend void *CMyClass::f();  // C2863  
};  
```