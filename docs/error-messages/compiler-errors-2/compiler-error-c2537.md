---
title: 編譯器錯誤 C2537 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2537
dev_langs:
- C++
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6100f77d3a1487bfa1eb12a78ac8187cec43fe64
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2537"></a>編譯器錯誤 C2537
'specifier': 不合法的連結規格  
  
 可能的原因：  
  
1.  不支援的連結規範。 支援只"C"的連結規範。  
  
2.  一個以上的函式多載函式集合中指定"C"連結。 這是不允許的。  
  
 下列範例會產生 C2537:  
  
```  
// C2537.cpp  
// compile with: /c  
extern "c" void func();   // C2537  
extern "C" void func2();   // OK  
```