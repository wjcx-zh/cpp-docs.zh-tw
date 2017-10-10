---
title: "編譯器錯誤 C2537 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2537
dev_langs:
- C++
helpviewer_keywords:
- C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 610fe53b68ccfa9f0ec187356a737e67837656a4
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

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
