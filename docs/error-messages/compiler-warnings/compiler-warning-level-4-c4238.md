---
title: 編譯器警告 （層級 4） C4238 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4238
dev_langs:
- C++
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 06dbec01da8d1b47cb7b93c90a22ae5266e9b4c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4238"></a>編譯器警告 (層級 4) C4238
使用非標準擴充： 類別右值當做左值  
  
 與舊版的 Visual c + + 中，Microsoft 擴充功能的相容性 (**/Ze**) 可讓您使用的類別類型，如右值的內容中亦隱含或明確地取得其位址。 在某些情況下，如下列範例中，這可能十分危險。  
  
## <a name="example"></a>範例  
  
```  
// C4238.cpp  
// compile with: /W4 /c  
struct C {  
   C() {}  
};  
  
C * pC = &C();   // C4238  
```  
  
 這種用法會導致 ANSI 相容性錯誤 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。