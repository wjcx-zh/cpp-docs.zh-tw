---
title: 編譯器警告 （層級 1） C4114 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4114
dev_langs:
- C++
helpviewer_keywords:
- C4114
ms.assetid: 3983e1c6-e8bb-46dc-8894-e1827db48797
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 78402d4487eecde00c55ea5e0aad913d97226325
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4114"></a>編譯器警告 （層級 1） C4114
相同類型的限定詞已經使用多次  
  
 型別宣告或定義使用類型限定詞 (**const**， `volatile`，**簽署**，或`unsigned`) 一次以上。 這會導致警告，以搭配 Microsoft 擴充功能 (/Ze) 而在 ANSI 相容性 (/Za) 錯誤。  
  
 下列範例會產生 C4114:  
  
```  
// C4114.cpp  
// compile with: /W1 /c  
volatile volatile int i;   // C4114  
```  
  
 下列範例會產生 C4114:  
  
```  
// C4114_b.cpp  
// compile with: /W1 /c  
static const int const * ii;   // C4114  
static const int * const iii;   // OK  
```