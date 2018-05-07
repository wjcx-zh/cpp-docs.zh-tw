---
title: 編譯器警告 C4936 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4936
dev_langs:
- C++
helpviewer_keywords:
- C4936
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dcf9f32a4a1b1e43cb4bd69c754e3ae3a98bff3d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4936"></a>編譯器警告 C4936
以 /clr 或 /clr:pure 編譯時才支援這個 __declspec  
  
 **/Clr: pure** Visual Studio 2015 中的編譯器選項已被取代。  
  
 已使用 `__declspec` 修飾詞，但該 `__declspec` 修飾詞僅有在以 [/clr](../../build/reference/clr-common-language-runtime-compilation.md) 選項之一來編譯時才有效。  
  
 如需詳細資訊，請參閱 [appdomain](../../cpp/appdomain.md) 和 [處理序](../../cpp/process.md)。  
  
 C4936 總是發出錯誤。  您可以使用 [warning](../../preprocessor/warning.md) pragma 來停用 C4936。  
  
 下列範例會產生 C4936：  
  
```  
// C4936.cpp  
// compile with: /c  
// #pragma warning (disable : 4936)  
__declspec(process) int i;   // C4936  
__declspec(appdomain) int j;   // C4936  
```