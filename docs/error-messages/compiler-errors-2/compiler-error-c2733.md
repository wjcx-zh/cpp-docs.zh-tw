---
title: 編譯器錯誤 C2733 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2733
dev_langs:
- C++
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc1857cd800dd2d395754b9ae95094d9f57aad27
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2733"></a>編譯器錯誤 C2733
多載函式 'function' 不允許第二個 C 連結  
  
 使用 C 連結宣告一個以上多載函式。 使用 C 連結時，只有一種指定的函式可以是外部。 多載函式有相同的未裝飾的名稱，因為它們不能與 C 程式。  
  
 下列範例會產生 C2733:  
  
```  
// C2733.cpp  
extern "C" {  
   void F1(int);  
}  
  
extern "C" {  
   void F1();   // C2733  
   // try the following line instead  
   // void F2();  
}  
```