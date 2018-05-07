---
title: 編譯器錯誤 C2165 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2165
dev_langs:
- C++
helpviewer_keywords:
- C2165
ms.assetid: b108313b-b8cb-4dce-b2ec-f2b31c9cdc87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db8d434993ad913efca3fdff58fb7ed9cc0715e5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2165"></a>編譯器錯誤 C2165
'keyword': 無法修飾指向資料的指標  
  
 `__stdcall`、 `__cdecl`或 `__fastcall` 關鍵字嘗試修改資料的指標。  
  
 下列範例會產生 C2165：  
  
```  
// C2165.cpp  
// compile with: /c  
char __cdecl *p;   // C2165  
char *p;   // OK  
```