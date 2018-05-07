---
title: 編譯器錯誤 C3748 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3748
dev_langs:
- C++
helpviewer_keywords:
- C3748
ms.assetid: 6fe71a0a-dd93-4ce6-9729-b9616360cf34
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: de3d943db70b0e13b727f9c3e680f6cccc7f446e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3748"></a>編譯器錯誤 C3748
'interface': managed 的介面不能引起事件  
  
 [__Event](../../cpp/event.md)關鍵字不能出現的介面。  
  
 下列範例會產生 C3748:  
  
```  
// C3748.cpp  
__interface I {  
// try the following line instead  
// struct I {  
   __event void f();   // C3748  
};  
  
int main() {  
}  
```