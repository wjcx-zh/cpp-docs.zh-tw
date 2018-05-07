---
title: 編譯器錯誤 C3641 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3641
dev_langs:
- C++
helpviewer_keywords:
- C3641
ms.assetid: e8d3613e-5e8d-46fe-a516-eb7d1de7cd21
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 496ff73822dcc1c886fbd2020f8ec6b8a5a9a2f7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3641"></a>編譯器錯誤 C3641
'function': 無效的呼叫慣例 'calling_convention' 以 /clr 編譯的函式： pure 或 /clr: safe  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 只有[__clrcall](../../cpp/clrcall.md)呼叫慣例則允許使用[/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
 下列範例會產生 C3641:  
  
```  
// C3641.cpp  
// compile with: /clr:pure /c  
void __cdecl f() {}   // C3641  
```