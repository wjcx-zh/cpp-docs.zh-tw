---
title: 編譯器錯誤 C2194 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2194
dev_langs:
- C++
helpviewer_keywords:
- C2194
ms.assetid: df6e631c-0062-4844-9088-4cc7a0ff879f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 61a2ca45df170245fae0795adc006349c1b62fb2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169240"
---
# <a name="compiler-error-c2194"></a>編譯器錯誤 C2194
'identifier': 是文字區段  
  
 `data_seg` Pragma 會使用區段名稱搭配使用`code_seg`。  
  
 下列範例會產生 C2194:  
  
```  
// C2194.cpp  
// compile with: /c  
#pragma code_seg("MYCODE")  
#pragma data_seg("MYCODE")   // C2194  
#pragma data_seg("MYCODE2")   // OK  
```