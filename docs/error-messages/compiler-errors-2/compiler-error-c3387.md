---
title: 編譯器錯誤 C3387 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3387
dev_langs:
- C++
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5469088b6707faa31e1d49157dcbc9991ffb7060
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3387"></a>編譯器錯誤 C3387
'member': __declspec （dllexport) /\__declspec(dllimport) 無法套用至成員 managed 或 WinRT 類型  
  
 `dllimport`和[dllexport](../../cpp/dllexport-dllimport.md) `__declspec`修飾詞不是有效的 managed 成員或 Windows 執行階段類型。  
  
 下列範例會產生 C3387，並示範如何修正此問題：  
  
```  
// C3387a.cpp  
// compile with: /clr /c  
ref class X2 {  
   void __declspec(dllexport) mf() {   // C3387  
   // try the following line instead  
   // void mf() {  
   }  
};  
```