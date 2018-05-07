---
title: 編譯器警告 （層級 1） C4552 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4552
dev_langs:
- C++
helpviewer_keywords:
- C4552
ms.assetid: ebbbb5ee-1c19-45bd-b386-41a19630fc76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3b58d33286163050db533fed00d27abe8903e9f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4552"></a>編譯器警告 (層級 1) C4552
'operator': 運算子無效;必須是具有副作用的運算子  
  
 如果運算式陳述式為上方的運算子沒有副作用，但它可能是運算式的發生錯誤。  
  
 若要覆寫這個警告，請將放在括號中的運算式。  
  
 下列範例會產生 C4552:  
  
```  
// C4552.cpp  
// compile with: /W1  
int main() {  
   int i, j;  
   i + j;   // C4552  
   // try the following line instead  
   // (i + j);  
}  
```