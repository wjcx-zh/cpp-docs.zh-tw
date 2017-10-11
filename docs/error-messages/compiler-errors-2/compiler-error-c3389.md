---
title: "編譯器錯誤 C3389 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3389
dev_langs:
- C++
helpviewer_keywords:
- C3389
ms.assetid: eaaffe17-23f2-413c-b1ad-f7220cfa1334
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 561359afcd9cf694369bd1addb4f641a33a3f989
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3389"></a>編譯器錯誤 C3389
__declspec(keyword) 不能以 /clr: pure 或 /clr: safe  
  
 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 A [__declspec](../../cpp/declspec.md)修飾詞表示每個處理序狀態。  [/clr: pure](../../build/reference/clr-common-language-runtime-compilation.md)表示每個[appdomain](../../cpp/appdomain.md)狀態。  因此，宣告的變數`keyword` **__declspec**修飾詞和編譯**/clr: pure**不允許。  
  
 下列範例會產生 C3389:  
  
```  
// C3389.cpp  
// compile with: /clr:pure /c  
__declspec(dllexport) int g2 = 0;   // C3389  
```
