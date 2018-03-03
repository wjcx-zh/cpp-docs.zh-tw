---
title: "編譯器警告 （層級 3） C4334 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4334
dev_langs:
- C++
helpviewer_keywords:
- C4334
ms.assetid: d845857f-bc95-4faf-a079-626a0cf935ba
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7218caa399aec0bd1b9755fb6d0942991732121e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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