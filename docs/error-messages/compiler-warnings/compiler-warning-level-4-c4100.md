---
title: 編譯器警告 （層級 4） C4100 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4100
dev_langs:
- C++
helpviewer_keywords:
- C4100
ms.assetid: 478ed97d-e502-49e4-9afb-ac2a6c61194b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4d3cf831590af2e1f2f7cd13d93c9d13ba217e11
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292801"
---
# <a name="compiler-warning-level-4-c4100"></a>編譯器警告 (層級 4) C4100
'identifier': 未參考的型式參數  
  
 函式主體中未參考的型式參數。 未參考的參數已忽略。  
  
 C4100 同時發出，當程式碼會呼叫解構函式上的其他方式參考基本類型的參數。  這是 Visual c + + 編譯器的限制。  
  
 下列範例會產生 C4100:  
  
```  
// C4100.cpp  
// compile with: /W4  
void func(int i) {   // C4100, delete the unreferenced parameter to  
                     //resolve the warning  
   // i;   // or, add a reference like this  
}  
  
int main()  
{  
   func(1);  
}  
```