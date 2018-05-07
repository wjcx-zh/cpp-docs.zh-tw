---
title: 編譯器錯誤 C2658 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2658
dev_langs:
- C++
helpviewer_keywords:
- C2658
ms.assetid: 638368e8-7893-4a14-abec-13c768a9543a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8e071e070b259dee7293d607d292a51ee608b71c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2658"></a>編譯器錯誤 C2658
'member': 匿名結構/等位中的重複定義  
  
 兩個匿名結構或等位包含具有相同的識別項，但不同類型的成員宣告。 在下[/Za](../../build/reference/za-ze-disable-language-extensions.md)，您也會取得此錯誤，具有相同的識別項和類型成員。  
  
 下列範例會產生 C2658:  
  
```  
// C2658.cpp  
// compile with: /c  
struct X {  
   union { // can be struct too  
      int i;  
   };  
   union {  
      int i;   // Under /Za, C2658  
      // int i not needed here because it is defined in the first union  
   };  
};  
  
struct Z {  
   union {  
      char *i;  
   };  
  
   union {  
      void *i;   // C2658 redefinition of 'i'  
      // try the following line instead  
      // void *ii;  
   };  
};  
```