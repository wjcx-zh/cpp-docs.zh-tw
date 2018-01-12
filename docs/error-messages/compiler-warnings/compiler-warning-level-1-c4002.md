---
title: "編譯器警告 （層級 1） C4002 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4002
dev_langs: C++
helpviewer_keywords: C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c11b40f29ccbd0e58afdce08463a87dc71181d6a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4002"></a>編譯器警告 (層級 1) C4002
巨集 'identifier' 的實質參數太多  
  
 巨集中的實際參數數目超出巨集定義中的正式參數數目。 前置處理器會收集額外的參數，但會在巨集展開期間忽略這些巨集。  
  
 不正確地使用 [Variadic Macros](../../preprocessor/variadic-macros.md)時，會發生 C4002。  
  
 下列範例會產生 C4002：  
  
```  
// C4002.cpp  
// compile with: /W1  
#define test(a) (a)  
  
int main() {  
   int a = 1;  
   int b = 2;  
   a = test(a,b);   // C4002  
   // try..  
   a = test(a);  
}  
```  
  
 針對 Visual Studio .NET 2003 所進行的編譯器一致性工作，也可能會導致這個錯誤：不再接受巨集中的額外逗號。  
  
 在巨集中，編譯器不再接受額外逗號。 對於 Visual C++ 的 Visual Studio .NET 2003 和 Visual Studio .NET 版本中都有效的程式碼，移除額外的逗號。  
  
```  
// C4002b.cpp  
// compile with: /W1  
#define F(x,y)  
int main()  
{  
   F(2,,,,,,3,,,,,,)   // C4002  
   // Try the following line instead:  
   // F(2,3)  
}  
```