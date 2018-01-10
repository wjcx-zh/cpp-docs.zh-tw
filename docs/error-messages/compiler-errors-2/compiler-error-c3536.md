---
title: "編譯器錯誤 C3536 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3536
dev_langs: C++
helpviewer_keywords: C3536
ms.assetid: 8d866075-866b-49eb-9979-ee27b308f7e3
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1bf9e3baacf7028d37c08db095a16d136f99d361
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3536"></a>編譯器錯誤 C3536
'symbol': 無法在初始化之前使用。  
  
 在初始化之前，無法使用指定的符號。 實際上，這表示不能使用變數來初始化它自己。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  無法初始化本身的變數。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3536，因為每個變數會初始化與其本身。  
  
```  
// C3536.cpp  
// Compile with /Zc:auto  
int main()  
{  
   auto a = a;     //C3536  
   auto b = &b;    //C3536  
   auto c = c + 1; //C3536  
   auto* d = &d;   //C3536  
   auto& e = e;    //C3536  
   return 0;  
};  
```  
  
## <a name="see-also"></a>請參閱  
 [auto 關鍵字](../../cpp/auto-keyword.md)