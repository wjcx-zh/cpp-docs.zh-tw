---
title: 編譯器錯誤 C2531 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2531
dev_langs:
- C++
helpviewer_keywords:
- C2531
ms.assetid: c49afe15-55f8-4dc8-ac01-bf653622a7db
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af944c56dfd579c608edd48b22925480f16d05c4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2531"></a>編譯器錯誤 C2531
'identifier': 位元欄位不合法的參考  
  
 不允許位元欄位的參考。  
  
 下列範例會產生 C2531:  
  
```  
// C2531.cpp  
// compile with: /c  
class P {  
   int &b1 : 10;   // C2531  
   int b2 : 10;   // OK  
};  
```