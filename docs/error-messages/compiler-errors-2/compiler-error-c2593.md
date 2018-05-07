---
title: 編譯器錯誤 C2593 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2593
dev_langs:
- C++
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e419416266e0e3c4ebff8190b3b26b1c43c9ba0f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2593"></a>編譯器錯誤 C2593
'運算子 identifier' 模稜兩可  
  
 多載的運算子定義一個以上可能的運算子。  
  
 如果您在上一個或多個實際的參數使用明確轉換，可能會修正這個錯誤。  
  
 下列範例會產生 C2593:  
  
```  
// C2593.cpp  
struct A {};  
struct B : A {};  
struct X {};  
struct D : B, X {};  
void operator+( X, X );  
void operator+( A, B );  
D d;  
  
int main() {  
   d +  d;         // C2593, D has an A, B, and X   
   (X)d + (X)d;    // OK, uses operator+( X, X )  
}  
```  
  
 這個錯誤可能因序列化浮點變數使用`CArchive`物件。 編譯器識別`<<`運算子作為模稜兩可。 只有基本 c + + 類型`CArchive`可以序列化為固定大小的型別`BYTE`， `WORD`， `DWORD`，和`LONG`。 所有的整數類型必須轉換成這些類型的其中一個，進行序列化。 浮點類型必須使用封存`CArchive::Write()`成員函式。  
  
 下列範例示範如何將浮點變數 (`f`) 到封存`ar`:  
  
```  
ar.Write(&f, sizeof( float ));  
```