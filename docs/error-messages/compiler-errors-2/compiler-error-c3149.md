---
title: 編譯器錯誤 C3149 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3149
dev_langs:
- C++
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c0441a7aebf86139aedbd5e45a7645db0a90b37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248504"
---
# <a name="compiler-error-c3149"></a>編譯器錯誤 C3149
'type': 不能使用這個型別此處卻沒有最上層的 'char'  
  
 未正確指定宣告。  
  
 比方說，您可能已定義在全域範圍的 CLR 型別，並嘗試建立類型的變數定義的一部分。 因為不允許 CLR 類型的全域變數，編譯器會產生 C3149。  
  
 若要解決這個錯誤，宣告函式或類型定義內的 CLR 型別的變數。  
  
 下列範例會產生 C3149:  
  
```  
// C3149.cpp  
// compile with: /clr  
using namespace System;  
int main() {  
   // declare an array of value types   
   array< Int32 ^> IntArray;   // C3149  
   array< Int32>^ IntArray2;   // OK  
}  
```  
  
 下列範例會產生 C3149:  
  
```  
// C3149b.cpp  
// compile with: /clr /c  
delegate int MyDelegate(const int, int);  
void Test1(MyDelegate m) {}   // C3149  
void Test2(MyDelegate ^ m) {}   // OK  
```  
