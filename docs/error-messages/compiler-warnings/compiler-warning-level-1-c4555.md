---
title: 編譯器警告 （層級 1） C4555 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4555
dev_langs:
- C++
helpviewer_keywords:
- C4555
ms.assetid: 50b286c1-f7bf-4292-b1fa-baaac9538611
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 019423685bb92ddb4b9d4bafc58bb4ba4eb2d708
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4555"></a>編譯器警告 (層級 1) C4555
運算式無效; 必須是具有副作用的運算式  
  
 這個警告會通知您的運算式時沒有任何作用。  
  
 此警告預設為關閉。 如需詳細資訊，請參閱 [預設為關閉的編譯器警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 。  
  
 例如:   
  
```  
// C4555.cpp  
// compile with: /W1  
#pragma warning(default:4555)  
  
void func1()  
{  
   1;   // C4555  
}  
  
void func2()  
{  
   int x;  
   x;   // C4555  
}  
  
int main()  
{  
}  
```