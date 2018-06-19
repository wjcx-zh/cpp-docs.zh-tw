---
title: 編譯器警告 （層級 1） C4945 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4945
dev_langs:
- C++
helpviewer_keywords:
- C4945
ms.assetid: 6d2079ea-dc59-4611-bc68-9a22c06f7587
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8218c0ce387f70cb13a4074a3b3d008a72b1fe3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291475"
---
# <a name="compiler-warning-level-1-c4945"></a>編譯器警告 (層級 1) C4945
'symbol': 無法匯入來自 'assembly2' 的符號： 因為 'symbol' 已從另一個組件 'assembly1' 匯入  
  
 從參考組件匯入的符號，但該符號已經匯入從另一個參考的組件。 請勿參照其中一個組件，或變更其中一個組件中的符號名稱。  
  
 下列範例會產生 C4945。  
  
```  
// C4945a.cs  
// compile with: /target:library  
// C# source code to create a dll  
public class ClassA {  
   public int i;  
}  
```  
  
 然後，  
  
```  
// C4945b.cs  
// compile with: /target:library  
// C# source code to create a dll  
public class ClassA {  
   public int i;  
}  
```  
  
 然後，  
  
```  
// C4945c.cpp  
// compile with: /clr /LD /W1  
#using "C4945a.dll"  
#using "C4945b.dll"   // C4945  
```