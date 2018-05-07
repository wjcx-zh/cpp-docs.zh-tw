---
title: 編譯器警告 （層級 3） C4334 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4334
dev_langs:
- C++
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f26749c968c3cac18b509046633ba3d91d15a4be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-3-c4334"></a>編譯器警告 (層級 3) C4334
'operator': 32 位元移位的結果以隱含方式轉換為 64 位元 （為 64 位元位移？）  
  
 32 位元移位的結果已隱含地轉換成 64 位元和 64 位元位移是編譯器懷疑這些檔案。  若要解決這個警告，請使用 64 位元位移，或是明確轉換為 64 位元位移結果。  
  
## <a name="example"></a>範例  
 下列範例會產生 C4334。  
  
```  
// C4334.cpp  
// compile with: /W3 /c  
void SetBit(unsigned __int64 *p, int i) {  
   *p |= (1 << i);   // C4334  
   *p |= (1i64 << i);   // OK  
}  
```