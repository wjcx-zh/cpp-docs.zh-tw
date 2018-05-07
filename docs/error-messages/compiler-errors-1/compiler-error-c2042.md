---
title: 編譯器錯誤 C2042 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2042
dev_langs:
- C++
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5b0442371b210f40d58a10b6bf1107979ea88db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2042"></a>編譯器錯誤 C2042
signed 及 unsigned 關鍵字是互斥的  
  
 關鍵字 `signed` 和 `unsigned` 用於單一宣告中。  
  
 下列範例會產生 C2042：  
  
```  
// C2042.cpp  
unsigned signed int i;   // C2042  
```  
  
 可能的解決方式：  
  
```  
// C2042b.cpp  
// compile with: /c  
unsigned int i;  
signed int ii;  
```