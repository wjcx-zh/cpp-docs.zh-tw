---
title: "編譯器錯誤 C3387 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3387
dev_langs:
- C++
helpviewer_keywords:
- C3387
ms.assetid: c54d9925-ed14-4976-b8db-e8d4dc84e536
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 79b38cd1793509c92ec2d2941fbb3eb2e7121ee7
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

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
