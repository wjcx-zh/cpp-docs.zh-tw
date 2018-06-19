---
title: 編譯器錯誤 C2233 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2233
dev_langs:
- C++
helpviewer_keywords:
- C2233
ms.assetid: 236bdf0b-9607-4f26-a249-d8def0b1333c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21a44ef30d328826b1ab4a968d4746b5274006b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33171070"
---
# <a name="compiler-error-c2233"></a>編譯器錯誤 C2233
'identifier': 包含大小為零的陣列物件的陣列不合法  
  
 陣列中的每個物件必須包含至少一個項目。  
  
 下列範例會產生 C2233:  
  
```  
// C2233.cpp  
// compile with: /c  
class A {  
   char somearray[1];  
};  
  
class B {  
   char zeroarray[];  
};  
  
A array[100];   // OK  
B array2[100];   // C2233  
```