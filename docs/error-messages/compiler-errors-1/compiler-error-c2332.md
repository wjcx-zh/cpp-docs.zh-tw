---
title: "編譯器錯誤 C2332 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2332
dev_langs:
- C++
helpviewer_keywords:
- C2332
ms.assetid: fb05cd68-e271-4bea-9fb7-ef4edb0a26ac
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9f3ad7e48a1c83f268770d8d66930dc95b18f1a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2332"></a>編譯器錯誤 C2332
'typedef': 遺漏標記名稱  
  
 編譯器發現不完整的類型定義。  
  
 下列範例會產生 C2332:  
  
```  
// C2332.cpp  
// compile with: /c  
struct S {  
   int i;  
};  
  
typedef struct * pS;   // C2332  
typedef struct S* pS;   // OK  
  
int get_S_i(pS p) {  
   return p->i;  
}  
```