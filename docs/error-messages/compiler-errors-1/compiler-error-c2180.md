---
title: "編譯器錯誤 C2180 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2180
dev_langs:
- C++
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fdea36a8c6c7bf5e561c161dc7180ab3b563c0ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2180"></a>編譯器錯誤 C2180
控制運算式具有類型 'type'  
  
 `if`、`while`、`for` 或 `do` 陳述式中的控制運算式，是轉換成 `void` 的運算式。 若要修正此問題，請將控制運算式變更為會產生 `bool` 的運算式或可轉換成 `bool` 的類型。  
  
 下列範例會產生 C2180：  
  
```  
// C2180.c  
  
int main() {  
   while ((void)1)   // C2180  
      return 1;  
   while (1)         // OK  
      return 0;  
}  
```