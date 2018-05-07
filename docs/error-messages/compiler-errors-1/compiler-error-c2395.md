---
title: 編譯器錯誤 C2395 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2395
dev_langs:
- C++
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 411a8d62de801591ff6a90a7bf74f3b2cfe67c7a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2395"></a>編譯器錯誤 C2395
'your_type::operator'op'' : CLR or WinRT 運算子無效。 至少一個參數必須是下列類型：'T'、'T%'、'T&'、'T^'、'T^%'、'T^&'，其中 T = 'your_type'  
  
 Windows 執行階段或 Managed 類型中的運算子沒有至少一個參數，其類型與運算子傳回值的類型相同。  
  
 下列範例會產生 C2395，並示範如何修正此問題：  
  
```  
// C2395.cpp  
// compile with: /clr /c  
value struct V {  
   static V operator *(int i, char c);   // C2395  
  
   // OK  
   static V operator *(V v, char c);  
   // or  
   static V operator *(int i, V& rv);  
};  
```