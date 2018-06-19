---
title: 編譯器警告 （層級 4） C4208 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4208
dev_langs:
- C++
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b61f8b0a6a0ac61982bee79abb81f083d40a48f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33292359"
---
# <a name="compiler-warning-level-4-c4208"></a>編譯器警告 (層級 4) C4208
使用非標準擴充： delete [exp]-評估 exp 運算式但忽略  
  
 搭配 Microsoft 擴充功能 (/Ze)，您可以刪除使用括號與值的陣列[delete 運算子](../../cpp/delete-operator-cpp.md)。 會忽略的值。  
  
```  
// C4208.cpp  
// compile with: /W4  
int main()  
{  
   int * MyArray = new int[18];  
   delete [18] MyArray;      // C4208  
   MyArray = new int[18];  
   delete [] MyArray;        // ok  
}  
```  
  
 這類值都無效 ANSI 相容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。