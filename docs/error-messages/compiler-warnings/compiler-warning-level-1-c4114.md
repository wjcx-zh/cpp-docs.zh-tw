---
title: 編譯器警告 （層級 1） C4114 |Microsoft Docs
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
ms.openlocfilehash: 9969f58b24defdb3dfa8a96437769d0b19e4569e
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/16/2018
ms.locfileid: "42541764"
---
# <a name="compiler-warning-level-1-c4114"></a>編譯器警告 （層級 1） C4114
相同類型的限定詞已經使用多次  
  
 類型宣告或定義使用類型限定詞 (**const**， **volatile**，**簽署**，或**不帶正負號**) 一次以上。 這會導致警告，以搭配 Microsoft 擴充功能 (/Ze) 與 ANSI 相容性 (/Za) 時發生。  
  
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
