---
title: 編譯器警告 （層級 1） C4508 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4508
dev_langs:
- C++
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 53f152c2f3573e5f3bd7b8e9be0603ed6d3f11bb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4508"></a>編譯器警告 (層級 1) C4508
'function': 函式應傳回值。'void' 傳回假設的類型  
  
 函式有沒有指定的傳回類型。 在此情況下，也應該引發 C4430 和編譯器實作的 C4430 （預設值是 int） 所報告的修正。  
  
 若要解決這個警告，明確宣告函式的傳回型的別。  
  
 下列範例會產生 C4508:  
  
```  
// C4508.cpp  
// compile with: /W1 /c  
#pragma warning (disable : 4430)  
func() {}   // C4508  
void func2() {}   // OK  
```