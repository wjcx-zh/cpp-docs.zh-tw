---
title: 編譯器錯誤 C2372 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2372
dev_langs:
- C++
helpviewer_keywords:
- C2372
ms.assetid: 406bea63-c8d3-4231-9d26-c70af6980840
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 864162b02a2c7575809887bb638bb703219eea71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2372"></a>編譯器錯誤 C2372
'identifier': 重複定義;不同類型的間接取值  
  
 已使用不同的衍生型別定義的識別項。  
  
 下列範例會產生 C2326：  
  
```  
// C2372.cpp  
// compile with: /c  
extern int *fp;  
extern int fp[];   // C2372  
extern int fp2[];   // OK  
```