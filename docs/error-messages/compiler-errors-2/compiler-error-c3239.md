---
title: "編譯器錯誤 C3239 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3239
dev_langs:
- C++
helpviewer_keywords:
- C3239
ms.assetid: 22a518b7-020f-4f3c-9963-a094667fd1ac
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e356befb8fa8492afd888a2d534f4c1e2c018c5d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3239"></a>編譯器錯誤 C3239
'type': Common Language Runtime 不允許內部/Pin 指標的指標  
  
 編譯器發現無效的類型。  
  
 下列範例會產生 C3229：  
  
```  
// C3239.cpp  
// compile with: /clr  
int main() {  
   interior_ptr<int>* pip0;   // C3239  
  
   // OK  
   int * pip1;  
   interior_ptr<int> pip2;  
   int ** pip;  
}  
```