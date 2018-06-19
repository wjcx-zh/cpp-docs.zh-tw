---
title: 編譯器錯誤 C2032 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2032
dev_langs:
- C++
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1db268222f3b9f7ca6f9ce297680866185e6661d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33167212"
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