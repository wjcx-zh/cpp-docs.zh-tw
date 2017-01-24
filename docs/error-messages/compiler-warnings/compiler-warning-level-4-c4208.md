---
title: "編譯器警告 (層級 4) C4208 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4208"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4208"
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4208
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用非標準的擴充：delete \[exp\] \- 會評估 exp 運算式但結果會忽略不用  
  
 使用 Microsoft 擴充功能 \(\/Ze\)，您可以用 [delete 運算子](../../cpp/delete-operator-cpp.md)配合括號內的值刪除陣列。  值會被忽略。  
  
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
  
 這些值在 ANSI 相容性 \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\) 下是無效的。