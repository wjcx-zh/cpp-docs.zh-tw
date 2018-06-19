---
title: 編譯器錯誤 C2362 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2362
dev_langs:
- C++
helpviewer_keywords:
- C2362
ms.assetid: 7aafecbc-b3cf-45a6-9ec3-a17e3f222511
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53b0b77930acba6ecf2d0f3c6748ba52e9b28e0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33222172"
---
# <a name="compiler-error-c2362"></a>編譯器錯誤 C2362
'identifier' 的初始化會略過 'goto 標籤'  
  
 編譯時[/Za](../../build/reference/za-ze-disable-language-extensions.md)，跳至標籤將導致無法進行初始化識別項。  
  
 除非放在不輸入，區塊中宣告，不能跳過的初始設定式宣告或變數尚未初始化。  
  
 下列範例會產生 C2326：  
  
```  
// C2362.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   int i = 1;      // C2362, initialization skipped  
label1:;  
}  
```  
  
 可能的解決方式：  
  
```  
// C2362b.cpp  
// compile with: /Za  
int main() {  
   goto label1;  
   {  
      int j = 1;   // OK, this block is never entered  
   }  
label1:;  
}  
```