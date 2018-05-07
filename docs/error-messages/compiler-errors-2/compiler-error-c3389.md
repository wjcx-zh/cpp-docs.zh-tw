---
title: 編譯器錯誤 C3389 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3389
dev_langs:
- C++
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6f0f60a1096c070d28be3b7af161bbb924fb20dd
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3389"></a>編譯器錯誤 C3389
__declspec(keyword) 不能以 /clr: pure 或 /clr: safe  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 A [__declspec](../../cpp/declspec.md)修飾詞表示每個處理序狀態。  [/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)表示每個[appdomain](../../cpp/appdomain.md)狀態。  因此，宣告的變數`keyword` **__declspec**修飾詞和編譯 **/clr: pure**不允許。  
  
 下列範例會產生 C3389:  
  
```  
// C3389.cpp  
// compile with: /clr:pure /c  
__declspec(dllexport) int g2 = 0;   // C3389  
```