---
title: 編譯器警告 （層級 1） C4553 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4553
dev_langs:
- C++
helpviewer_keywords:
- C4553
ms.assetid: d8aacbe0-3cb5-4367-a6e5-fd7e28f0ff9d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8633a9cf3eb8f825f1bfd131db6c1dfd2f8d6159
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33277877"
---
# <a name="compiler-warning-level-1-c4553"></a>編譯器警告 (層級 1) C4553
'operator': 運算子無效;您是否想 'operator'？  
  
 如果運算式陳述式為上方的運算子沒有副作用，但它可能是運算式的發生錯誤。  
  
 下列範例會產生 C4553:  
  
```  
// C4553.cpp  
// compile with: /W1  
int func()  
{  
   return 0;  
}  
  
int main()  
{  
   int i;  
   i == func();   // C4553  
   // try the following line instead  
   // i = func();  
}  
```