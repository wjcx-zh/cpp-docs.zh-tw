---
title: "編譯器警告 （層級 1） C4311 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4311
dev_langs:
- C++
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5ae2f4b7d7c9ac57f5bdc3fd219c7682e0ec639d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4311"></a>編譯器警告 (層級 1) C4311
'variable' : 指標從 'type' 到 'type' 截斷  
  
 此警告會偵測 64 位元指標截斷問題。 例如，如果程式碼是針對 64 位元架構而編譯的，若指派給 `int` (32 位元)，指標 (64 位元) 的值將會被截斷。 如需詳細資訊，請參閱[使用指標的規則](http://msdn.microsoft.com/library/windows/desktop/aa384242)。  
  
 其他與警告 C4311 的常見原因的相關資訊，請參閱[常見編譯器錯誤](http://msdn.microsoft.com/library/windows/desktop/aa384160)。  
  
 下列程式碼範例會在針對 64 位元目標而編譯時產生 C4311，並接著示範如何修正此問題：  
  
```  
// C4311.cpp  
// compile by using: cl /W1 C4311.cpp  
int main() {  
   void* p = &p;  
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets  
   unsigned long long j = (unsigned long long) p;   // OK  
}  
  
```