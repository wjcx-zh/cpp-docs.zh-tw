---
title: "編譯器錯誤 C3386 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3386
dev_langs:
- C++
helpviewer_keywords:
- C3386
ms.assetid: 93fa8c33-0f10-402b-8eec-b0a217a1f8dc
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8b912d1d75ae120f993c3641ff2e2b561910b4aa
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3386"></a>編譯器錯誤 C3386
'type': __declspec （dllexport) /\__declspec(dllimport) 無法套用至 managed 或 WinRTtype  
  
 `dllimport`和[dllexport](../../cpp/dllexport-dllimport.md) `__declspec`修飾詞不是有效的 managed 或 Windows 執行階段類型。  
  
 下列範例會產生 C3386，並示範如何修正此問題：  
  
```  
// C3386.cpp  
// compile with: /clr /c  
ref class __declspec(dllimport) X1 {   // C3386  
// try the following line instead  
// ref class X1 {  
};  
```
