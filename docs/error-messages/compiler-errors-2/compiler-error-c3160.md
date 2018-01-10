---
title: "編譯器錯誤 C3160 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3160
dev_langs: C++
helpviewer_keywords: C3160
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 6a8257f2615a23855d324ac211c848ac1a428e16
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3160"></a>編譯器錯誤 C3160
'pointer': Managed 或 WinRT 類別的資料成員不能有這種類型  
  
 內部記憶體回收指標可能指向 Managed 或 WinRT 類別的內部。 因為它們比完整物件指標更慢，而且需要記憶體回收行程進行特殊處理，您無法將內部 Managed 指標宣告為類別的成員。  
  
 下列範例會產生 C3160：  
  
```  
// C3160.cpp  
// compile with: /clr  
ref struct A {  
   // cannot create interior pointers inside a class  
   interior_ptr<int> pg;   // C3160  
   int g;   // OK  
   int* pg2;   // OK  
};  
  
int main() {  
   interior_ptr<int> pg2;   // OK  
}  
```  
