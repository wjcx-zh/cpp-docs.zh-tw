---
title: 編譯器錯誤 C3395 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3395
dev_langs:
- C++
helpviewer_keywords:
- C3395
ms.assetid: 26a9ebc9-ed97-47ce-b436-19aa2bcf6e50
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 202162ecac8907852ca621599f5306884e59ae98
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3395"></a>編譯器錯誤 C3395
'function': __declspec （dllexport） 無法套用至函式\__clrcall 呼叫慣例  
  
 `__declspec(dllexport)` 和[__clrcall](../../cpp/clrcall.md)不相容。  如需詳細資訊，請參閱[dllexport、 dllimport](../../cpp/dllexport-dllimport.md)。  
  
 下列範例會產生 C3395:  
  
```  
// C3395.cpp  
// compile with: /clr /c  
  
__declspec(dllexport) void __clrcall Test(){}   // C3395  
void __clrcall Test2(){}   // OK  
__declspec(dllexport) void Test3(){}   // OK  
```