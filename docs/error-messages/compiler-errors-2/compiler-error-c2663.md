---
title: "編譯器錯誤 C2663 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2663
dev_langs: C++
helpviewer_keywords: C2663
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a9efe20b4a80b9ff6f337d32acd35320125008dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
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