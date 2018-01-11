---
title: "編譯器警告 （層級 4） C4208 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4208
dev_langs: C++
helpviewer_keywords: C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aefe97e67c566418067c0a7bff594c42f89364b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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