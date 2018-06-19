---
title: 編譯器錯誤 C2663 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2663
dev_langs:
- C++
helpviewer_keywords:
- C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f39f516b32aaf1159d47726d01623e253ee8b383
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33235855"
---
# <a name="compiler-error-c2663"></a>編譯器錯誤 C2663
'function': 數字的多載包含有 'this' 指標不合法轉換  
  
 編譯器無法轉換`this`任何成員函式多載版本。  
  
 這個錯誤可能因叫用非`const`成員函式上的`const`物件。  可能的解決方式：  
  
1.  移除`const`從物件宣告。  
  
2.  新增`const`其中一個成員函式多載。  
  
 下列範例會產生 C2663:  
  
```  
// C2663.cpp  
struct C {  
   void f() volatile {}  
   void f() {}  
};  
  
struct D {  
   void f() volatile;  
   void f() const {}  
};  
  
const C *pcc;  
const D *pcd;  
  
int main() {  
   pcc->f();    // C2663  
   pcd->f();    // OK  
}  
```